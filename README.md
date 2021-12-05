# Download
`npm i svelte-aid`

# Import

`import { Image, Copy } from 'svelte-aid'`


## Image
Alternative to default img, loads images from opacity 0 and hides if broken

Required arguments:

`src`

Optional arguments:

`srcMobile` for a mobile version of the img (default as src)
`alt` like html alt
`classes` like css class
`loading` like html loading (default is `lazy`, can change to `eager`)

### Examples
`<Image src={"https://picsum.photos/1000"} alt={"random image"} classes={"object-cover rounded-md w-96"}>`

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

## Ticker
A horizontally running ticker

Required arguments:
`items` an array of strings to animate

Optional arguments:
`duration` in seconds (default `10s`)
`durationMobile` in seconds (default `20s`)
`classWrapper` css classes for the wrapper (default `absolute`, useful for position fixed and background color and padding)
`classParent` css classes for the parent of items (default `space-x-6`)
`classChild` css classes for individual item (default `inline-block`)

### Examples
```
<Ticker
    classChild={"text-xl text-white uppercase inline-block"}
    classParent={"space-x-10"}
    classWrapper={"fixed bottom-0 p-5 bg-black"}
    duration={"15s"}
/>
```