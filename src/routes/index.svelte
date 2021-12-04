<script lang="ts">
    import Image from '$lib/Image.svelte'
    import CopyText from '$lib/CopyText.svelte';
</script>
<div>Svelte Aid</div>

<div>Copy example</div>
<CopyText text={"this text will be copied"} useText={true} onCopyText={"Nice!"} color={"red"} colorActive={"green"} />

<div>Image example</div>


<Image alt={"random image"} src={"https://picsum.photos/1201/1080"} srcMobile={"https://picsum.photos/300"} classes={"w-full"} />