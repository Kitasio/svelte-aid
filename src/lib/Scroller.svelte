<script lang="ts">
    import { onMount } from "svelte";
    import { fade } from "svelte/transition";
    import { Image } from "svelte-aid"

    export let items = [
        {
            text: "1",
            img: "https://picsum.photos/1000/201",
            link: "https://www.youtube.com/watch?v=dQw4w9WgXcQ",
        },
        {
            text: "2",
            img: "https://picsum.photos/1000/202",
            link: "https://www.youtube.com/watch?v=dQw4w9WgXcQ",
        },
        {
            text: "3",
            img: "https://picsum.photos/1000/203",
            link: "https://www.youtube.com/watch?v=dQw4w9WgXcQ",
        },
    ];
    export let parentClass: string = "py-7 md:py-10";
    export let textClass: string = "";
    export let wrapperClass: string = "";

    let triItems = [...items, ...items, ...items];

    onMount(() => {
        items = [...items, ...items, ...items];
        for (let i = 0; i < triItems.length; i++) {
            triItems[i]["shown"] = false;
        }
        console.log(items);
        gsap.registerPlugin(ScrollTrigger);
        gsap.registerPlugin(ScrollToPlugin);

        gsap.to(window, {
            duration: 1,
            scrollTo: "#item" + Math.floor(items.length / 3).toString(),
        });

        for (let i = 0; i < items.length; i++) {
            gsap.to(`#item${i}`, {
                duration: 0.5,
                color: "white",
                scrollTrigger: {
                    start: "-2px center",
                    end: "bottom center",
                    trigger: `#item${i}`,
                    toggleActions: "restart reverse restart reverse",
                    snap: 0.5,
                    onToggle: (self) => (triItems[i]["shown"] = self.isActive),
                },
            });
        }
    });
</script>

<svelte:head>
    <script
        src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.8.0/gsap.min.js"></script>
    <script
        src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.8.0/ScrollTrigger.min.js"></script>
    <script
        src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.8.0/ScrollToPlugin.min.js"></script>
</svelte:head>

<div class="w-full border-t border-black {wrapperClass}">
    {#each triItems as i, index (index)}
        <div
            id="item{index}"
            class="relative border-b border-black {parentClass}"
        >
            <a href={i.link}>
                {#if i["shown"]}
                    <div transition:fade>
                        <Image
                            src={i.img}
                            classes={"absolute w-full top-0 h-full object-cover"}
                        />
                    </div>
                {/if}
                <div class="flex justify-between mx-5">
                    <div class="z-20 relative {textClass}">{i.text}</div>
                    <svg
                        class="fill-current text-white w-5 h-5 z-20 relative"
                        xmlns="http://www.w3.org/2000/svg"
                        fill="white"
                        viewBox="0 0 24 24"
                        stroke="currentColor"
                    >
                        <path
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            stroke-width="2"
                            d="M14 5l7 7m0 0l-7 7m7-7H3"
                        />
                    </svg>
                </div>
            </a>
        </div>
    {/each}
</div>
