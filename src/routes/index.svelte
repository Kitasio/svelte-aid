<script lang="ts">
    import Image from '$lib/Image.svelte'
    import CopyText from '$lib/CopyText.svelte';
</script>
<div>Svelte Aid</div>

<div>Copy example</div>
<CopyText text={"this text will be copied"} useText={true} onCopyText={"Nice!"} color={"red"} colorActive={"green"} />

<div>Image example</div>


<div style="margin-top: 500px;">
    <Image alt={"random image"}  src={"https://picsum.photos/1201/1080"} classes={"class"} />
</div>
<div style="margin-top: 500px;">
    <Image alt={"random image"}  src={"https://picsum.photos/1202/1080"} classes={"class"} />
</div>
<div style="margin-top: 500px;">
    <Image alt={"random image"}  src={"https://picsum.photos/1203/1080"} classes={"class"} />
</div>
<div style="margin-top: 500px;">
    <Image alt={"random image"}  src={"https://picsum.photos/1204/1080"} classes={"class"} />
</div>
<div style="margin-top: 500px;">
    <Image alt={"random image"}  src={"https://picsum.photos/1205/1080"} classes={"class"} />
</div>