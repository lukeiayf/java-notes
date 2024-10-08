- For direct parent -> child you can use props
```
<Parent>
	<Child :props="some-props">
<Parent />
```

at Child component you register the props

```
const props = defineProps(['foo'])
```

- If you need to alter data sent to the child and display it in the parent you can use emits
```
<!-- Child component -->
<button @click="$emit('someEvent')">Click Me</button>
```

then at the parent component you listen to the emitted event

```
<MyComponent @some-event="callback" />
```

- For deeply nested components you can use provide and inject