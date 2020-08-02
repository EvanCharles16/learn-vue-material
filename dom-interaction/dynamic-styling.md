### Dynamic Styling with CSS Classes - Basics

HTML

```

 <div id="app">
    <div class="demo" @click="attachRed = !attachRed" :class="{ red : attachRed }" ></div>
    <div class="demo" :class="{ red : attachRed }"></div>
    <div class="demo"></div>
 </div>
```

CSS

```
.demo {
    width : 100px;
    height : 100px;
    background-color : gray;
    display : inline-block;
    margin : 10px;
}

.red {
    background-color : red
}

.green {
    background-color : green
}

.blue {
    background-color : blue
}
```

Javascript

```
new Vue({
    el : '#app',
    data : {
        attachRed : false,
    }
})
```

Output <br/>

Both of the div changes color when clicked , because they share the same property, which is attachRed.

---

### Dynamic Styling with CSS Classes - Objects

HTML

```

 <div id="app">
    <div class="demo" @click="attachRed = !attachRed" :class="divClasses" ></div>
    <div class="demo" :class="{ red : attachRed }"></div>
    <div class="demo"></div>
 </div>
```

CSS

```
.demo {
    width : 100px;
    height : 100px;
    background-color : gray;
    display : inline-block;
    margin : 10px;
}

.red {
    background-color : red
}

.green {
    background-color : green
}

.blue {
    background-color : blue
}
```

Javascript

```
new Vue({
    el : '#app',
    data : {
        attachRed : false,
    },
    computed : {
        divClasses : function(){
            return {
                red : this.attachRed,
                blue : !this.attachRed,
            }
        }
    }
})
```

Output <br/>

Both of the div changes color to red when clicked , because they share the same property, which is attachRed. And Default color is blue.

---

### Dynamic Styling with CSS Classes - Names

HTML

```
   <div id="app">
      <div class="demo" @click="attachRed = !attachRed" :class="divClasses" ></div>
      <div class="demo" :class="{ red : attachRed }"></div>
      <div class="demo" :class="[color, {red : attachRed}]"></div>

      <hr/>

      <input type="text" v-model="color" />
   </div>
```

CSS

```
.demo {
    width : 100px;
    height : 100px;
    background-color : gray;
    display : inline-block;
    margin : 10px;
}

.red {
    background-color : red
}

.green {
    background-color : green
}

.blue {
    background-color : blue
}
```

Javascript

```
new Vue({
    el : '#app',
    data : {
        attachRed : false,
        color : 'green',
    },
    computed : {
        divClasses : function(){
            return {
                red : this.attachRed,
                blue : !this.attachRed,
            }
        }
    }
})
```

Key is a class , value is a condition

<p>Example : :class="[color , {red : attachRed} ]"</p>

---

Check this out => https://jsfiddle.net/smax/gowg40ym/

---

### Setting Styles Dynamically (Without CSS Classes)

HTML

```
  <div id="app">
      <div class="demo" :style="{backgroundColor : color}"></div>
     <div class="demo" :style="myStyle"></div>
      <div class="demo"></div>

      <hr/>

      <input type="text" v-model="color" />
      <input type="text" v-model="width" />
   </div>
```

CSS

```
.demo {
    width : 100px;
    height : 100px;
    background-color : gray;
    display : inline-block;
    margin : 10px;
}

.red {
    background-color : red
}

.green {
    background-color : green
}

.blue {
    background-color : blue
}
```

Javascript

```
new Vue({
    el : '#app',
    data : {
       color : 'gray',
       width : 100,
    },
    computed : {
			myStyle : function(){
				return {
        	backgroundColor : this.color,
          width : this.width + 'px'
        }
			}
    }
})
```

Output <br/>

We can changes the color and width using the two ways binding , :style

---

Check this out => https://jsfiddle.net/smax/3rvdLq5y/

---

### Styling Elements with the Array Syntax

HTML

```
  <div id="app">
      <div class="demo" :style="{backgroundColor : color}"></div>
     <div class="demo" :style="myStyle"></div>
      <div class="demo" :style=" [myStyle, {height : width + 'px' } ] "></div>

      <hr/>

      <input type="text" v-model="color" />
      <input type="text" v-model="width" />
   </div>
```

CSS

```
.demo {
    width : 100px;
    height : 100px;
    background-color : gray;
    display : inline-block;
    margin : 10px;
}

.red {
    background-color : red
}

.green {
    background-color : green
}

.blue {
    background-color : blue
}
```

Javascript

```
new Vue({
    el : '#app',
    data : {
       color : 'gray',
       width : 100,
    },
    computed : {
			myStyle : function(){
				return {
        	backgroundColor : this.color,
          width : this.width + 'px'
        }
			}
    }
})
```

Output <br/>

This how you can use styles and classes and bind directly to both classes and styles using the different syntaxes to pass the styles and classes you want to pass.

---
