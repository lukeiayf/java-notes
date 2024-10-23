**Composition API**

- `beforeCreate()`: called at the setup() method 
- `onMounted()` :  register a callback after the component has been mounted
- `onUpdated()`: register a callback after the component has updated its DOM due to a change in a reactive state
- `onUnmounted()`: register a callback after the component has been unmounted
- `onBeforeMount()`: register a callback before the component is mounted
- `onBeforeUpdate()`: registers a hook to be called right before the component is about to update its DOM tree due to a reactive state change.
- `onBeforeUnmount()`: registers a hook to be called right before a component instance is to be unmounted.
- **`onUnmounted()`**:   called **after the component has been unmounted** from the DOM. It is used to perform final cleanup.

Options API:

- `created()`: Called after the component is created, but before it is mounted to the DOM.
- `mounted()`: Called after the component has been added to the DOM.
- `updated()`: Called when reactive data causes the component to re-render.
- `beforeDestroy()`: Called just before the component is destroyed.
