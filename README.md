# sparklines.css

![Sparklines.css Preview](https://raw.githubusercontent.com/sfearl1/sparklines/main/assets/sparklines.png)

## Installation

To use sparklines.css in your project:

1. Install the package via npm:

```bash
npm install sparklines.css
```

2. Register the worklet:

```javascript
if ('paintWorklet' in CSS) {
    CSS.paintWorklet.addModule('path/to/sparklines.js');
}
```

3. Customize it in your CSS:

```css
@layer sparklines {

    :root {
        --chart-color: #dcff52;
        --chart-data: 110, 55, 62, 15, 48, 19, 30, 27, 11, 23, 21, 29, 12, 38, 25, 17, 5, 20, 32, 28, 13, 36, 24, 87, 45, 90, 58, 47, 11, 23;
        --max-data-points: 30;
        --bar-width: 2;
        --line-width: 1;
        --fill-type: gradient;
        --fill-opacity: 0.5;
        --gradient-opacity: 0.5;
        --padding-vertical: 10;
        --padding-horizontal: 20;
    }

    .chart {
        background: paint(sparklines);

        &.line {
            --chart-type: line; 
        }

        &.bar {
            --chart-type: bar; 
        }
    }
}
```

4. Use it in your HTML (example combined with tailwind for utility styles):

```html
<div class="p-6 flex flex-row">
    <div class="chart line h-[75px] w-1/2 place-self-center"></div>
    <div class="chart bar h-[75px] w-1/2 place-self-center"></div>
</div>
```

## Browser Support

If you need to support browsers that do not natively support the CSS Paint API, you can use a polyfill:

```javascript
if (!CSS["paintWorklet"]) {
    await import("https://unpkg.com/css-paint-polyfill");
} else {
    CSS.paintWorklet.addModule('https://your-cdn-url/sparklines.js');
}
```
    
For more information on browser support for the CSS Paint API, you can check the compatibility on [can I use](https://caniuse.com/css-paint-api).

## Demo

Live demo [here](https://sfearl1.github.io/sparklines).

## Contributing

Feel free to submit issues or pull requests to improve the package.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.