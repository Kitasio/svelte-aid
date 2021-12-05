<script lang="ts">
    export let items: ArrayLike<string> = [
        "item 1",
        "item 2",
        "item 3",
        "item 4",
    ];
    export let duration: string = "10s";
    export let durationMobile: string = "20s";

    export let classWrapper: string = "absolute";
    export let classParent: string = "space-x-6";
    export let classChild: string = "inline-block";
</script>

<div class="ticker-wrap {classWrapper}">
    <div class="ticker {classParent}" style="--duration: {duration}; --duration-mobile: {durationMobile}">
        {#each items as i, index (index)}
            <div class="{classChild}">{i}</div>
        {/each}
    </div>
</div>

<style>
    @-webkit-keyframes ticker {
        0% {
            -webkit-transform: translate3d(0, 0, 0);
            transform: translate3d(0, 0, 0);
            visibility: visible;
        }
        100% {
            -webkit-transform: translate3d(-100%, 0, 0);
            transform: translate3d(-100%, 0, 0);
        }
    }
    @keyframes ticker {
        0% {
            -webkit-transform: translate3d(0, 0, 0);
            transform: translate3d(0, 0, 0);
            visibility: visible;
        }
        100% {
            -webkit-transform: translate3d(-100%, 0, 0);
            transform: translate3d(-100%, 0, 0);
        }
    }
    .ticker-wrap {
        width: 100%;
        overflow: hidden;
        padding-left: 100%;
        box-sizing: content-box;
    }
    .ticker-wrap .ticker {
        display: inline-block;
        white-space: nowrap;
        padding-right: 100%;
        box-sizing: content-box;
        -webkit-animation-iteration-count: infinite;
        animation-iteration-count: infinite;
        -webkit-animation-timing-function: linear;
        animation-timing-function: linear;
        -webkit-animation-name: ticker;
        animation-name: ticker;
        -webkit-animation-duration: var(--duration-mobile);
        animation-duration: var(--duration-mobile);
    }
    @media (min-width: 640px) {
        .ticker-wrap .ticker {
            display: inline-block;
            white-space: nowrap;
            padding-right: 100%;
            box-sizing: content-box;
            -webkit-animation-iteration-count: infinite;
            animation-iteration-count: infinite;
            -webkit-animation-timing-function: linear;
            animation-timing-function: linear;
            -webkit-animation-name: ticker;
            animation-name: ticker;
            -webkit-animation-duration: var(--duration);
            animation-duration: var(--duration);
        }
    }
</style>
