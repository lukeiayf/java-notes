### 1. **What is the Composition API in Vue 3, and how does it differ from the Options API?**

**Answer:** The Composition API in Vue 3 is a new way to organize and structure code in Vue components. It allows developers to encapsulate logic into reusable functions, known as composables, rather than being tied to specific component options like `data`, `methods`, `computed`, etc., used in the Options API.

Key differences:

- **Logic Reusability:** The Composition API allows better logic reusability, as related pieces of code can be grouped together in functions rather than being spread across various component options.
- **TypeScript Support:** Composition API has better TypeScript integration, as it enables strong typing and inference when using reactive properties.
- **Code Organization:** Instead of dealing with large, monolithic components, the Composition API lets you break code into smaller, more manageable parts.

### 2. **How does `ref` work in the Composition API, and what are some common use cases?**

**Answer:** `ref` is used to declare reactive state in the Composition API. When you wrap a value with `ref`, Vue makes it reactive, meaning Vue will track changes to that value and update the DOM accordingly when the value changes.

```
import { ref } from 'vue';

const count = ref(0); // Reactive reference
function increment() {
  count.value++;
}

```
Common use cases:

- **Simple State Management:** Declaring and tracking primitive values like numbers, strings, or booleans.
- **DOM References:** `ref` can be used to reference DOM elements for direct manipulation.
- **Reactivity in Templates:** You need to access the `.value` of a `ref` when you want to use it in templates or other parts of the Composition API.

### 3. **What is `reactive` in Vue 3, and how is it different from `ref`?**

**Answer:** `reactive` is used to create reactive objects in Vue 3. Unlike `ref`, which wraps a primitive value in an object with a `.value` property, `reactive` is designed to work directly with objects and arrays.
```
import { reactive } from 'vue';

const user = reactive({
  name: 'Lucas',
  age: 30,
});

```
**Key Differences:**

- **Ref for primitives:** Use `ref` when you want to track a primitive value like a string, number, or boolean.
- **Reactive for objects/arrays:** Use `reactive` for complex objects or arrays. With `reactive`, you can directly mutate the object properties, and Vue will track the changes.

### 4. **How does `script setup` simplify the Composition API?**

**Answer:** The `script setup` syntax in Vue 3 is a compiler macro that simplifies the Composition API by allowing developers to write more concise code. It removes the need for the `setup` function and automatically handles variable exposure to the template.

**Advantages:**

- **Less Boilerplate:** No need for a return statement or the `setup` function itself.
- **More Readable:** More concise code and better readability.
- **Automatic Imports:** Components and composables declared in `script setup` are automatically available in the template.

### 5. **How does TypeScript integrate with Vue 3 and the Composition API?**

**Answer:** Vue 3 offers built-in TypeScript support, and it integrates seamlessly with the Composition API. You can strongly type component props, data, methods, and computed properties.

**Example using TypeScript in `script setup`:**
```
<script setup lang="ts">
import { ref } from 'vue';

const count = ref<number>(0);

function increment(): void {
  count.value++;
}
</script>

```
**Key Features:**

- **Typed Props:** You can define prop types using TypeScript interfaces or types.
- **Typed Refs:** You can specify the type of the value inside `ref`.
- **Return Types:** Functions and methods can be typed to ensure the correct return values.

### 6. **What are composables in Vue 3, and how are they used?**

**Answer:** Composables are reusable functions that leverage the Composition API to encapsulate stateful logic and can be shared across components. They allow code to be modular and reused throughout the application.

**Example of a composable:**
```
// useCounter.ts
import { ref } from 'vue';

export function useCounter() {
  const count = ref(0);
  const increment = () => count.value++;

  return { count, increment };
}

```
Using the composable:
```
<script setup>
import { useCounter } from './useCounter';

const { count, increment } = useCounter();
</script>

```

### 7. **How do you declare and validate props in a Vue 3 component using TypeScript?**

**Answer:** In Vue 3 with TypeScript, you can use `defineProps` to declare props and enforce typing.

**Example:**
```
<script setup lang="ts">
interface Props {
  title: string;
  count: number;
}

const props = defineProps<Props>();
</script>

<template>
  <h1>{{ props.title }}</h1>
  <p>{{ props.count }}</p>
</template>

```

### 8. **How would you structure a large-scale Vue.js application, and what best practices would you follow?**

**Answer:** In a large-scale Vue.js application, structuring the project in a modular and maintainable way is essential for scalability and ease of development. Here's how I would approach it:

- **Modular Architecture:** Split the application into reusable modules or features (e.g., user, dashboard, auth) that are self-contained and can be lazy-loaded.
- **Use Vuex or Pinia for State Management:** For global state management, use Vuex or Pinia, but ensure that you follow the single responsibility principle. Use modules to split state into smaller, more manageable pieces.
- **Composables for Reusable Logic:** Use the Composition API to create composable functions that encapsulate logic and can be reused across components.
- **Routing:** Use `vue-router` to define routes and implement lazy-loading to reduce the initial bundle size.
- **Folder Structure:** Organize components, services, composables, and store modules into clearly defined folders like `/components`, `/composables`, `/views`, `/services`, `/store`.
- **Code Splitting:** Use dynamic imports for lazy loading components and routes to improve performance.
- **Testing:** Write unit and integration tests using Vitest or Jest for core components and critical logic.
- **TypeScript:** Use TypeScript to ensure type safety and better tooling support for catching errors early.

### 9. **How would you optimize the performance of a Vue.js application?**

**Answer:** Optimizing the performance of a Vue.js application requires a combination of techniques to reduce load times, minimize resource usage, and enhance the user experience:

- **Lazy Loading and Code Splitting:** Use lazy loading to break your app into smaller chunks that load on-demand, especially for routes and components that are not immediately needed.
- **Memoization and Caching:** Use `computed` properties for expensive operations and ensure caching where appropriate to avoid unnecessary recomputations.
- **Debounce and Throttle:** Implement debouncing and throttling in event listeners (like for search inputs or scroll events) to limit how often expensive operations are executed.
- **Virtual Scrolling:** Use virtual scrolling libraries for large lists to only render visible elements, improving performance in apps with infinite scroll or large datasets.
- **Optimization of Rendering:** Avoid unnecessary re-renders by carefully managing state and not binding components to reactive properties that don't need frequent updates. You can also use `v-once` for static content.
- **Optimize Component Updates:** Use `watchEffect` or `watch` sparingly to avoid over-watching properties that can cause performance degradation.
- **Tree Shaking and Minification:** Use build tools like Webpack or Vite to tree-shake unused code and minify JS/CSS, ensuring the app's bundle size is minimized.
- **SSR (Server-Side Rendering):** For performance optimization on the initial load, SSR with Vue 3’s built-in support can significantly improve time to interactive (TTI).
- **Use Web Workers:** Offload heavy computations to Web Workers to prevent the main thread from blocking.

### 10. **Can you explain the trade-offs between using Vuex and Pinia for state management?**

**Answer:** Vuex has been the traditional state management library for Vue.js, but Pinia has gained popularity with Vue 3 due to its more modern API, better TypeScript support, and simpler usage.

**Vuex Pros:**

- **Mature and Well-Established:** Vuex has been around longer, with robust documentation and a larger community of users.
- **Modular Architecture:** Supports splitting the state into modules to keep the store manageable.
- **Strict Mutation Rules:** Vuex enforces immutability by requiring state mutations to happen only through mutations, making state management more predictable.

**Pinia Pros:**

- **Better TypeScript Support:** Pinia was designed with TypeScript in mind, providing better type inference and tooling out of the box.
- **Simpler API:** Pinia’s API is more intuitive and concise, relying less on boilerplate code.
- **Direct Composition API Integration:** Pinia works seamlessly with Vue 3’s Composition API, making it easier to use in modern Vue apps.
- **No Mutations:** Pinia doesn’t require the use of mutations, allowing state changes directly in actions, making the code simpler to manage.
- **SSR Ready:** Pinia has first-class support for server-side rendering with Vue 3.

**Trade-offs:**

- **Complexity:** Vuex can introduce complexity with its strict mutation pattern, especially in simpler apps. Pinia is more flexible but may trade off some of that strictness for simplicity.
- **Performance:** For larger applications with a lot of state, Vuex’s mutation-based approach can sometimes make it easier to track changes. Pinia is more flexible but may require developers to be more cautious about managing state changes.

### 11. **How do you manage complex forms with validation in Vue 3 using TypeScript?**

**Answer:** Managing complex forms in Vue 3 can be done efficiently by using libraries like `vee-validate` or `@vuelidate/core`, both of which offer great support for reactive forms and TypeScript.

### 12. **Explain the use of Suspense in Vue 3 and how you would implement it in a TypeScript project?**

**Answer:** Vue 3’s `Suspense` is a built-in feature that allows components to wait for asynchronous data to be resolved before rendering. This is particularly useful when fetching data from an API or loading a component asynchronously.

**Implementation:**

- `Suspense` works with async setup functions or components that return promises. If a component is wrapped with `Suspense`, Vue will automatically delay rendering until the async logic is resolved.
### 13. **What are some common anti-patterns in Vue.js development that you avoid?**

**Answer:** As a senior developer, it’s crucial to avoid anti-patterns that can lead to maintenance or performance issues. Some common anti-patterns include:

- **Tight Coupling Between Components:** Relying heavily on `props` and `events` can lead to tightly coupled components. Instead, use Vuex/Pinia or provide/inject for state sharing.
- **Mutating Props:** Changing props directly inside a child component instead of using `emit` or Vuex actions for proper state management.
- **Overusing Watchers:** Using too many `watch` properties can lead to performance degradation. Instead, prefer `computed` properties or `watchEffect` to handle reactive logic when possible.
- **Monolithic Components:** Not breaking down large components into smaller, reusable parts, making the application harder to maintain and extend.
- **Direct DOM Manipulation:** Avoid directly interacting with the DOM using `document.querySelector`. Instead, rely on Vue’s reactivity and lifecycle hooks to manage state changes and DOM updates.
### **14. How would you handle large amounts of data on a Vue application?**

There are a lot of approaches that can be made to handle large volumes of data on a vue application, some examples are:

 **Data Fetching and State Management**
 
- Using a centralized state management solution like `Pinia` (or Vuex) can help keep your application's state predictable and scalable. With Pinia, you can manage data in a store and make it reactive and available across components.

**Pagination and Infinite Scrolling**

- If the data is too large to load all at once, use **pagination** or **infinite scrolling** to load and display it in chunks. This reduces the initial load and improves performance.

**Virtualized Lists (Lazy Loading / Windowing)**

- For very large datasets, you can use **virtualized lists** to render only the visible portion of the dataset. This greatly improves performance by reducing the DOM footprint.
- Libraries like [Vue Virtual Scroller](https://github.com/Akryum/vue-virtual-scroller) work this way.

**Lazy Loading of Data**

- Using debounce(wait until a set time to call the function) and throttle for processing data that depends on user input ,such as search filters.

**Web Workers for Heavy Computation**

- If you have CPU-intensive operations (such as filtering or processing a huge dataset), you can offload these tasks to **Web Workers**. This way, heavy tasks run in the background, preventing the UI from freezing.

**Caching Data**

- Using LocalStorage or service workers to cache data to avoid re-fetching it;

**Optimizing Re-renders**
 
 - Be mindful of reactivity and avoid unnecessary re-renders by properly using `watch`, `watchEffect`, and `computed` properties. Also, be careful with deeply reactive objects, and consider using shallow reactive state (`shallowRef`, `shallowReactive`) where appropriate.

### **15. What is Webpack?**

- It's a module bundler, used to put several .js files into a single one, parse them and bundle them. Based on that bundle optimizations can be applied depending on the use-case.
- Tree-shaking is finding unused modules/imports and eliminating them to get the smallest bundle size.
- In version 5 it is applied by default on building, but it can only work with static ES6 imports, so if you are using common.js for example it will not be caught in the tree-shake because the 'require' are basically functions executed at runtime.

### 16. **What is a dependency graph?**

 - It is a tree structure based on the entrypoint of our project that keeps track of all the modules and files in the project. It is used for the bundler to traverse and check for tree-shaking and optimization.

### 17. **What is CSS in JS?**

 - **CSS-in-JS** refers to a styling technique where CSS is written and applied within JavaScript code. Instead of keeping styles separate in `.css` files, CSS-in-JS allows developers to define and manage styles directly within their JavaScript or TypeScript code, typically at the component level.
 - The main advantages are:
	 - The styles are scoped by default
	 - Allow dynamic styling based on props, states or context
- Disavadvantages:
	- You cannot cache the style since its inside the js
	- It makes the js bundle bigger
	- The classes names generated are hashes so it makes debugging harder
 - For Vue a common css-in-js library is `vue-styled-components`
```
 <template>
  <StyledButton :primary="true">Click Me</StyledButton>
</template>

<script setup>
import styled from 'vue-styled-components';

// Define the props for the styled component
const buttonProps = {
  primary: Boolean
};

// Create a styled button component
const StyledButton = styled('button', buttonProps)`
  background-color: ${(props) => (props.primary ? 'blue' : 'gray')};
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;

  &:hover {
    background-color: ${(props) => (props.primary ? 'darkblue' : 'darkgray')};
  }
`;
</script>

```


### 18. **What is FCP(First Contentful Paint)?**

 - FCP stands for **First Contentful Paint**. It is a key performance metric in web development that measures the time it takes for the first piece of content to be rendered on the screen after a user navigates to a web page. This "content" can be text, images, or any other visible elements in the viewport.

**How FCP is Measured:**

- **FCP Timing**: It is recorded from the time the user initiates loading the page (e.g., by clicking a link) to the time the first content appears.
- **Content Types**: The first content could be anything, such as text, an image, or even a background image.
 
**Tools for Measuring FCP**:

- **Google Lighthouse**: Audits your web page and reports FCP times.
- **Chrome DevTools**: Provides a breakdown of different performance metrics including FCP.
- **Web Vitals**: Google's tool that tracks important web performance metrics like FCP.

**How to Improve FCP**:

- **Optimize CSS and JavaScript**: Minimizing and deferring non-critical resources can help speed up the rendering of content.
- **Lazy Loading**: Load images and other assets only when they are needed.
- **Use a CDN**: Serving your content from a CDN ensures that the assets are delivered faster.
- **Reduce Render-Blocking Resources**: Minimizing or deferring JavaScript and CSS that block rendering can speed up the FCP.

### 19. **Differences in cookies, local and session storage**

- Cookie -> up to 4kb and it is server and client side. You send the cookies through an HTTP request.
- Local Storage -> much higher storage and persist indeterminately, good for storing application state.
- Session Storage -> same as Local but it is cleared when browser or window is closed
### 20. **What are some frontend application optimizations?**

- Bundler like vite or webpack
- Most of the below is already taken care of by modern bundlers
- Polyfill to check for language specific support for browsers and add vanilla js instead if its not supported
- Compression with gzip
- MInification and Uglyfication, removing new line and variables to minimize code size
### 21. **How to handle and optimize big images?**
- Set minimum dimension
- Add compression and Image optimization libraries
- Ship as WebP
- Use Lazy Loading or load on scroll
- Use srcSet to ship different images depending on device/viewport

### 22. **What is a CDN?**
- Content Delivery Network
- A CDN distribution allows users to fetch assets from the closer edge location from them instead of the central node.
- You can set CDN from AWS CloudFront
### 23. **What are Micro Frontends?**
- Microfrontends are an architectural style where a web application is divided into smaller, independently developed, deployed, and managed frontend components or "mini-applications." Each microfrontend represents a specific feature or section of the UI, often built with different frameworks or libraries, and they communicate with each other to form a cohesive app.
- They are very complex and should be used when there are a lot of engineers working on a monolithic app
### 24. **What is SSR in Vue and when would you use it?**
- **Server-Side Rendering (SSR)** in Vue is when the HTML is rendered on the server before sending it to the client. It improves SEO, performance on slow connections, and user experience for large applications.
- Vue supports SSR via **Nuxt.js** or Vue's official SSR package. You would use SSR when SEO is critical, or when you want to improve the time to first meaningful paint for large apps.

