### Listening to Events

HTML

```
<div id="app">
    <button v-on:click="increase">Click me</button>
    <p>{{ counter }}</p>
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

<button v-on:click="increase">Click me</button>
<br/>
When we clicking the button , this will happen increment , started from 0

v-on => Opposite from v-bind (allows us to bind something in our template, to pass data to it), we bind to something better said we listen to something to recieve something from our template.

v-on also takes an argument and the argument is the name of the event we want to consume or we want listen to.

v-on:click , we also can use any DOM event existing for the button , like mouse enter, mouse leave, click, etc

---

### Getting Event Data from the Event Object

HTML

```
<div id="app">
    <p v-on:mousemove="updateCoordinate">Coordinates : {{ x }} / {{ y }}</p>
</div>
```

Javascript

```
new Vue({
    el : "#app',
    data : {
        x : 0,
        y : 0,
    },
    methods : {
        updateCoordinate : function(event){
            this.x = event.clientX;
            this.y = event.clientY;
        }
    }
})
```

Output

```
Coordinates : x / y

# When we move mouse or hover over it ,these coordinates updated.
```

---
