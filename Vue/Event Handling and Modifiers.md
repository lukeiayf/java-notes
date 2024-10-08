- If you have an event that is being propagated where it shouldn't like:
```
<div @click="doSomething">
	<span @click="doSomethingElse" />
</div>
```
 where clicking the span will also trigger the div event you can stop it using an event modifier like:
 - .stop
```
<div @click="doSomething">
	<span @click.stop="doSomethingElse" />
</div>
```
- .prevent (used to stop the submit event from reloading the page)
```
<form @submit.prevent="submit" />
```
