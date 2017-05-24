#   Vue Full Loading


Full overlay loading with spinner for Vue.

Perfect for performing a task in the background avoiding any other action on the screen.

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
|  `event-bus`          | Object    | <b>Default null</b> <br>Central event Bus  |
|  `event-show`         | String    | <b>Default 'show-full-loading'|
|  `event-hide`         | String    | <b>Default 'hide-full-loading'|


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
     :event-show="show-my-full-loading"
     :event-hide="hide-my-full-loading"
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
