- You can use ref() to transform a variable of a primitive type into a reactive property
```
const count = ref(0); //string, number, boolean
```
- For non-primitive types, or objects,such as an array you can use reactive()
```
const arr = reactive([])
```
*This is a vue convention, both can work for any type