#   Vue Full Loading


Full overlay loading with spinner for Vue.

Perfect for performing a task in the background avoiding user to performing any other action on the screen.

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


##  Examples

Include the component in your .vue file, `show` prop is required for the component to work. 
```
<template>
 <loading
     :show="show"
     :label="label">
 </loading>
</template>
```

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
