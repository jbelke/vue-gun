# Vue-Gun

A plugin to make Gun integration with Vue easier.

## Installation

`npm install vue-gun --save` or `yarn add vue-gun`.

Add the plugin:

```javascript
import VueGun from 'vue-gun';
Vue.use(VueGun, {
    gun: gun // your gun instance
});
```

## Initialize Gun

You can either pass in a `gun` instance fully initialized, or allow VueGun to initialize it for you:

```javascript
import VueGun from 'vue-gun';
import SEA from 'gun/sea'; // Required for SEA functions and user authentication 
Vue.use(VueGun, {
    gun: gun // must be passed in at `gun` key
});
```

Allow VueGun to handle initialization by passing in options:

```javascript
import VueGun from 'vue-gun';
Vue.use(VueGun, {
    peers: ['someurl.com:9000/gun']
});
```


## Usage

Access the `gun` instance with `this.$gun` inside of your Vue instance and components.

For instance inside your component, you might have this:

```javascript
mounted: function() {
        this.$gun.get('some path').map().on((node, key) => {

            // add results straight to the Vue component state
            // and get updates when nodes are updated by GUN
            this.vueState[key] = node;
        });
    },
```
