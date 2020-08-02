```
Known Options for Vue Instace

- el : connect DOM
- data : Store data to be used
- methods : Methods of this Vue Instance
- computed : Dependent Properties
- watch : Execute code upon data changes
```

### Writing Javascript Code in the Templates

HTML

```
<div id="app">
    <button v-on:click="increase">Click me</button>

    //Or

    <button v-on:click="counter++">Click me</button>

    <p>{{ counter * 2 > 10 ? 'Greater than 10' : 'Smaller than 10' }}</p>
</div>
```

Javascript

```
new Vue({
    el : "#app',
    data : {
        counter: 0,
    },
    methods : {
        increase : function(){
            this.counter++;
        }
    }
})
```

Output
<br/>

<button>Click Me</button> // Increment

We can write any valid javascript code as long as its only one expression and doesnt contain an if or in statement or a for loop or something like that.

---

### Using Two ways Binding

HTML

```
<div id="app">
    <input type="text" v-model="name" />
    <p>{{ name }}</p>
</div>
```

Javascript

```
new Vue({
    el : "#app',
    data : {
        name : 'Max',
    },
})
```

Data Binding - We are able to use

- String Interpolation ( {{ }} )
- v-bind (to bind two attributes)
- v-on (to listen to events)

---

Check this out => https://jsfiddle.net/smax/ut0tsbcu/

---

### Reacting to changes with Computed Properties

everything stored in computed can be used just like you use a property in the data object.

HTML

```
<div id="app">
   <button v-on:click="counter++">Increase</button>
   <button v-on:click="counter--">Decrease</button>
   <button v-on:click="secondCounter++">Increase Second</button>
   <p>Counter : {{ counter }} | {{ secondCounter }} </p>
   <p>Result : {{ result() }} | {{ output }}</p>
</div>
```

Javascript

```
new Vue({
    el : "#app',
    data : {
        counter : 0,
        secondCounter : 0,
    },
    computed : {
        output : function(){
            console.log('Computed')
            return this.counter > 5 ? 'Greater than 5' : 'Smaller than 5'
        }
    },
    methods : {
        result : function(){
            console.log('Methods')
            return this.counter > 5 ? 'Greater than 5' : 'Smaller than 5'
        }
    }
})
```

Output
<br/>

`When we clicked Increase button , this will executed 'Computed' and 'Methods' but when we clicked Increase Second button, this will executed only Methods.`

---

### An Alternative to Computed Properties : Watching for Changes

HTML

```
<div id="app">
   <button v-on:click="counter++">Increase</button>
   <button v-on:click="counter--">Decrease</button>
   <button v-on:click="secondCounter++">Increase Second</button>
   <p>Counter : {{ counter }} | {{ secondCounter }} </p>
   <p>Result : {{ result() }} | {{ output }}</p>
</div>
```

Javascript

```
new Vue({
    el : "#app',
    data : {
        counter : 0,
        secondCounter : 0,
    },
    computed : {
        output : function(){
            console.log('Computed')
            return this.counter > 5 ? 'Greater than 5' : 'Smaller than 5'
        }
    },
    watch : {
      counter : function(value){
         var vm = this;
         setTimeout(function(){
             vm.counter = 0;
         } , 2000)
      }
    },
    methods : {
        result : function(){
            console.log('Methods')
            return this.counter > 5 ? 'Greater than 5' : 'Smaller than 5'
        }
    }
})
```

Ouput <br/>

`Counter value will be reset after 2 seconds // counter = 0`

---

### Saving time with Shorthands

- v-on === @

Example : `v-on:click === @click` // Event Handling

- v-bind === :

Example : `v-bind:href === :href`
`v-bind:class === :class`

---

Check this out => https://jsfiddle.net/smax/yLjqxmw0/

---
