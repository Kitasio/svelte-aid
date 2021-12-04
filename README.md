# Download


`npm i svelte-aid`
---

# Import

`import { Image, Copy } from 'svelte-aid'`
---

## Image
Alternative to default img, loads images from opacity 0 and hides if broken

Required arguments:
`src`

Optional arguments:
`alt` like html alt
`classes` like css class
`loading` like html loading (default is `lazy`, can change to `eager`)

### Examples
`<Image src={"https://picsum.photos/1000"} alt={"random image"} classes={"object-cover rounded-md w-96"}>`
---

## CopyText
A button to copy text on click

Required arguments:
`text` is the text to copy on click

Optional arguments:
`useText` boolean to use animation of text (default false, will animate a check icon)
`onCopyText` if useText true - the text itself
`colorActive` the color on hover and animate (default blue)
`color` (default black)

### Examples
`<CopyText text={"this text will be copied"} useText={true} onCopyText={"Nice!"} color={"red"} colorActive={"green"} />`