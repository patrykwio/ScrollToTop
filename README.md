# ScrollToTop
VUE 2.x Component: Switches up your page view when scrolling down get tired ;) and You push the button.

# How its's works
- invisible on start
- shown when You move down
- hide when You are back on top

# How use it
Import component to Your project

```js
import ScrollToTop from "./components/ScrollToTop"; /* exaple path and import name - can use yours */
```

Use it in root html wrapper 

```html
<ScrollToTop/>
```

# Configuration

All is descripted in .vue file, look inside and fell free to change anything

```js
 data() {
      return {
          buttonText: "Go to Top", //inner text of button element
          isActive: false, // status false for invisible on beginning
          scrollActivatePossition: 300, //possition of activate point from top in pixels
          scrollStep: 10, // step distance resolution for moving (speed contol variable)
          scrollTimeout: 1 // step time resolution in miliseconds (speed contol variable)
      }
  },
```

