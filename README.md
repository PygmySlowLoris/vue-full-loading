#   Vue Full Loading


Full overlay with spinner for Vue.

Perfect for performing a task in the background avoiding any other action on the screen.
Can be easily handled by your <b>central event bus</b>

<p align="center">
<img width="600" src="https://raw.githubusercontent.com/PygmySlowLoris/vue-full-loading/master/demo.gif"/>
</p>

<a href="https://pygmyslowloris.github.io/vue-full-loading/"> Live Demo</a>

##  Installation

```
npm install vue-full-loading --save
```

##  Properties

| Properties            | Type      | Values     |
| :---------------      | :-------  | :--------- |
|  `label`              | String    | <b>Default 'Loading...' |
|  `show`               | Boolean   | <b>Default false</b> <br>Options: true or false.  |
|  `overlay`            | Boolean   | <b>Default true</b> <br>Options: true or false.  |
|  `overlay-class`      | String    | <b>Default 'white-overlay'   |
|  `loader-class`       | String    | <b>Default 'loader-wrapper'   |
|  `event-bus`          | Object    | <b>Default null</b> <br>Central event Bus  |
|  `event-show`         | String    | <b>Default 'show-full-loading'|
|  `event-hide`         | String    | <b>Default 'hide-full-loading'|

##  Slots

Want to add your own loading content/style? No problem, you can use the available slots to do so.

Available slots:
 * `loading-container` - This is the container for the loading text/spinner
 * `loading-text` -  Only for the loading text
 * `loading-spinner` - Only for the spinner

##  Examples

Include the component in your `.vue` file. 
```
<template>
 <loading
     :show="show"
     :label="label">
 </loading>
</template>
```

You also can manage this component by your eventBus with custom event names. 
```
<template>
 <loading
     :event-bus="myEventBus"
     event-show="show-my-full-loading"
     event-hide="hide-my-full-loading"
     :label="label">
 </loading>
</template>
```
> Notice that if no event names passed it will use the default ones.

Match your data with your components props.
```
<script>
import loading from 'vue-full-loading'

export default {
  components: {
    loading
  },
   data(){
       return {
           show: false,
           label: 'Loading...'
       }
   }
}
</script>
```
