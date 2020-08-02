### Rendering Lists with v-for

HTML

```
<script src="https://unpkg.com/vue.dist/vue.js"></script>

<div id="app">
    <ul>
        <li v-for="item in ingredients"> {{ item }} </li>
    </ul>
</div>

```

Javascript

```
new Vue ({
    el : '#app',
    data : {
        ingredients : ['meat', 'fruits', 'cookies']
    }
})

```

---

### Getting the current Index

HTML

```
<script src="https://unpkg.com/vue.dist/vue.js"></script>

<div id="app">
    <ul>
        <li v-for="(item, index) in ingredients"> {{ item }} ( {{ index }} ) </li>
    </ul>
</div>

```

Javascript

```
new Vue ({
    el : '#app',
    data : {
        ingredients : ['meat', 'fruits', 'cookies']
    }
})

```

---

### Using an Alternative v-for Syntax

HTML

```
<script src="https://unpkg.com/vue.dist/vue.js"></script>

<div id="app">
    <ul>
        <li v-for="(item, index) in ingredients"> {{ item }} ( {{ index }} ) </li>
    </ul>

    <template v-for="(item, index) in ingredients">
        <h1>{{item}}</h1>
        <p>{{index}}</p>
    </template>
</div>

```

Javascript

```
new Vue ({
    el : '#app',
    data : {
        ingredients : ['meat', 'fruits', 'cookies']
    }
})

```

---

### Looping through Objects

HTML

```
<script src="https://unpkg.com/vue.dist/vue.js"></script>

<div id="app">
    <ul>
        <li v-for="(item, index) in ingredients"> {{ item }} ( {{ index }} ) </li>
    </ul>

    <hr/>

    <ul>
        <li v-for="person in persons">
            <div v-for="(value, key, index) in person">{{ key }} : {{value}} ( {{ index}} )</div>
        </li>
    </ul>

    <hr/>

    <template v-for="(item, index) in ingredients">
        <h1>{{item}}</h1>
        <p>{{index}}</p>
    </template>
</div>

```

Javascript

```
new Vue ({
    el : '#app',
    data : {
        ingredients : ['meat', 'fruits', 'cookies'],
        persons : [
            {name : 'Max', age : 27, color : 'red'}
            {name : 'Anna', age : 'unknown', color : 'blue'}
        ]
    }
})

```

---

### Looping through a List of Number

HTML

```
<div id="app">
    <span v-for="n in 10">{{ n }}</span>
</div>


```

Output

```
123456789
```

---

### Keeping Track of Elements when using v-for

HTML

```
<script src="https://unpkg.com/vue.dist/vue.js"></script>

<div id="app">
    <ul>
        <li v-for="(item, index) in ingredients" :key="index"> {{ item }} ( {{ index }} ) </li>
    </ul>
    <button @click="ingredients.push('spices')">Add New</button>

    <hr/>

    <ul>
        <li v-for="person in persons">
            <div v-for="(value, key, index) in person">{{ key }} : {{value}} ( {{ index}} )</div>
        </li>
    </ul>

    <hr/>

    <template v-for="(item, index) in ingredients">
        <h1>{{item}}</h1>
        <p>{{index}}</p>
    </template>
</div>

```

Javascript

```
new Vue ({
    el : '#app',
    data : {
        ingredients : ['meat', 'fruits', 'cookies'],
        persons : [
            {name : 'Max', age : 27, color : 'red'},
            {name : 'Anna', age : 'unknown', color : 'blue'}
        ]
    }
})

```

---
