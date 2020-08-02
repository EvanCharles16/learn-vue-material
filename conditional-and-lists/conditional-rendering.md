### Conditional Rendering with v-if

HTML

```
<script src="https://unpkg.com/vue/dist/vue.js"></script>

<div id="app">
    <p v-if="show">You can see me!</p>
    <p>Do you also see me ?</p>
    <button @click="show = !show">Switch</button>
</div>

```

Javascript

```
new Vue ({
	el : '#app',
    data : {
		show : true,
	}
})

```

Try this out on https://jsfiddle.net/

Learn More at https://vuejs.org/v2/guide/conditional.html#v-else-if

---

### Using Alternative v-if Syntax

HTML

```
<script src="https://unpkg.com/vue/dist/vue.js"></script>

<div id="app">
    <p v-if="show">You can see me!</p>
    <p>Do you also see me ?</p>

    <template v-if="show">
        <h1>Heading</h1>
        <p>Inside a template</p>
    </template>

    <button @click="show = !show">Switch</button>
</div>

```

Javascript

```
new Vue ({
	el : '#app',
    data : {
		show : true,
	}
})

```

The Alternative ways to use v-if , at the template v-if , its effect all on the template.

---

### Dont Detach it with v-show

HTML

```
<script src="https://unpkg.com/vue/dist/vue.js"></script>

<div id="app">
    <p v-if="show">You can see me!</p>
    <p>Do you also see me ?</p>

    <template v-if="show">
        <h1>Heading</h1>
        <p>Inside a template</p>
    </template>

    <p v-show="show">Do you also see me ?</p>
    <button @click="show = !show">Switch</button>
</div>

```

Javascript

```
new Vue ({
	el : '#app',
    data : {
		show : true,
	}
})

```

v-show => if you dont want to detach it , use v-show to only hide it and not remove it entirely from the DOM.

---
