<script lang="ts">
    import Image from "$lib/Image.svelte";
    import CopyText from "$lib/CopyText.svelte";
    import Ticker from "$lib/Ticker.svelte";
    import Scroller from "$lib/Scroller.svelte";
</script>

<div>Svelte Aid</div>

<div>Scroller example</div>
<Scroller />

<div>Ticker example</div>
<Ticker
    classChild={"text-xl text-white uppercase inline-block"}
    classParent={"space-x-10"}
    classWrapper={"fixed bottom-0 p-5 bg-black"}
/>

<div>Copy example</div>
<CopyText
    text={"this text will be copied"}
    useText={true}
    onCopyText={"Nice!"}
    color={"red"}
    colorActive={"green"}
/>

<div>Image example</div>

<Image
    alt={"random image"}
    src={"https://picsum.photos/1201/1080"}
    srcMobile={"https://picsum.photos/300"}
    classes={"w-full"}
/>
