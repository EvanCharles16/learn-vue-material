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
  el: "#app",
  data: {
  	x : 0,
    y : 0,
  },
  methods: {
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

# When we hover over it ,these coordinates updated.
```

---

### Passing your own Argument with Events

HTML

```
<div id="app">
    <button v-on:click="increase(2, $event)">Click me</button>
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
        increase : function(step){
            this.counter += step;
        }
    }
})
```

Output

<button v-on:click="increase">Click me</button>
<br/>
2 => 4 => 6 => 8 => ...

\$event => Event Handling

---

### Modifying an Event with Event Modifiers

HTML

```
<div id="app">
    <p v-on:mousemove="updateCoordinate">Coordinates : {{ x }} / {{ y }} - <span v-on:mousemove.stop>DEATH SPOT</span></p>

    //or

    <p v-on:mousemove="updateCoordinate">Coordinates : {{ x }} / {{ y }} - <span v-on:mousemove="dummy">DEATH SPOT</span></p>

</div>
```

Javascript

```
new Vue({
  el: "#app",
  data: {
  	x : 0,
    y : 0,
  },
  methods: {
  	 updateCoordinate : function(event){
    	this.x = event.clientX;
        this.y = event.clientY;
	},
    {
        dummy : function(event){
            event.stopPropagation();
        }
    }
  }
})
```

Output

```
Coordinates : x / y - DEATH SPOT
```

So when we hover on DEATH SPOT , the Coordinate will stop

---

### Listening to Keybaord Events

HTML

```
<div id="app">
    <input type="text" v-on:keyup.enter.space="alertMe" />
</div>
```

Javascript

```
new Vue({
  el: "#app",
  data: {
  	x : 0,
    y : 0,
  },
  methods: {
  	 alertMe : function(){
           alert('Alert')
       }
  }
})
```

Output
<br/>

<input type="text" />

`so when we enter or space, there will have a alert 'Alert'`

<br/>

#### Key Modifiers

http://vuejs.org/v2/guide/events.html#Key-Modifiers

---
