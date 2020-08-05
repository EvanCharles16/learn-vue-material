### Multiple Vue Instance

HTML

```
<div id="app1">
  <h1>{{ title }}</h1>
  <button @click="show">Show Paragraph</button>
  <p v-if="showParagraph">New Paragraph</p>
</div>

<div id="app2">
  <h1>{{ title }}</h1>
  <button @click="onChange">Change something in Vue 1</button>
</div>
```

CSS

```
p {
  margin-bottom : 20px;
}

#app2 {
  margin: 20px 0
}
```

Javascript

```
var vm1 = new Vue({
	el : "#app1",
  data : {
		title : 'The Vue Instance',
    showParagraph : false,
	},
  methods : {
		show(){
			this.showParagraph = true;
      this.updateTitle("The Vue Instance(Updated)")
    },
    updateTitle(title){
			this.title = title
		}
	},
  computed : {
			lowercaseTitle(){
				return this.title.toLowerCase();
      }
		},
    watch : {
			title(value){
				alert("Title Changed, new Value :" + value)
			}
		}
})

vm1.newProp = "New Prop"
console.log(vm1)  // Add to the properties on Vue Instance

setTimeout(function(){
	vm1.title = "Change by Timer"
} ,3000)


var vm2 = new Vue({
	el : "#app2",
  data : {
		title : "The Second Instance"
	},
  methods : {
		onChange(){
			vm1.title = "Changed!"
		}
	}
})
```

Try it out on [JSFiddle](https://jsfiddle.net/)

---

### Look Closer at $el and $data

<br />
\$el => it refers to our template, it refers to our html code of that instance

\$data => is an object which holds our data properties, this is another way of accessing data from outside

Example : so while i can access the data by direcyly typing `vm1.title`, i could also type `$data.title` because \$data is the data block we passed here accessible from outside.

<br />
Vuejs doesnt create its own enclosed world, its normal Javascript code, it live in Javascript code and its able to interact with the javascript code around it.

---

### Placing \$ref and Using them on your Templates

HTML

```
<div id="app1">
  <h1 ref="heading">
    {{title}}
  </h1>

  <button @click="show" ref="myButton">Show Paragraph</button>
  <p v-if="showParagraph">New Paragraph</p>
</div>

<div id="app2">
  <h1>
  {{ title }}
  </h1>
  <button @click="onChange">
  Change something in Vue 1
  </button>
</div>
```

CSS

```
p {
  margin-bottom : 20px;
}

#app2 {
  margin: 20px 0
}
```

Javascript

```
data : {
	title : 'The Vue Instance',
    showParagraph : false,
},

var vm1 = new Vue({
	el : "#app1",
    data : data,
    methods : {
      show(){
        this.showParagraph = true;
        this.updateTitle("The Vue Instance(Updated)");
        this.$refs.myButton.innerText = "Button Changed"
        },
        updateTitle(title){
                this.title = title
            }
        },
    computed : {
                lowercaseTitle(){
                    return this.title.toLowerCase();
        }
            },
        watch : {
                title(value){
                    alert("Title Changed, new Value :" + value)
                }
            }
})

vm1.$refs.heading.innerText = "Something else"

setTimeout(function(){
	vm1.title = "Change by Timer"
  vm1.show();
} ,3000)


var vm2 = new Vue({
	el : "#app2",
  data : {
		title : "The Second Instance"
	},
  methods : {
		onChange(){
			vm1.title = "Changed!"
		}
	}
})
```

Try it out on [JSFiddle](https://jsfiddle.net/)

---

### Mounting a Template

HTML

```
<div id="app1">
  <h1 ref="heading">
    {{title}}
  </h1>

  <button @click="show" ref="myButton">Show Paragraph</button>
  <p v-if="showParagraph">New Paragraph</p>
</div>

<div id="app2">
  <h1>
  {{ title }}
  </h1>
  <button @click="onChange">
  Change something in Vue 1
  </button>
</div>

<div id="app3"></div>
```

CSS

```
p {
  margin-bottom : 20px;
}

#app2 {
  margin: 20px 0
}
```

Javascript

```
var data = {
	title : 'The Vue Instance',
    showParagraph : false,
}

var vm1 = new Vue({
  data : data,
  methods : {
		show(){
			this.showParagraph = true;
      this.updateTitle("The Vue Instance(Updated)");
      this.$refs.myButton.innerText = "Button Changed"
    },
    updateTitle(title){
			this.title = title
		}
	},
  computed : {
			lowercaseTitle(){
				return this.title.toLowerCase();
      }
		},
    watch : {
			title(value){
				alert("Title Changed, new Value :" + value)
			}
		}
})

vm1.$mount('#app1');
vm1.$refs.heading.innerText = "Something else"

setTimeout(function(){
	vm1.title = "Change by Timer"
  vm1.show();
} ,3000)


var vm2 = new Vue({
	el : "#app2",
  data : {
		title : "The Second Instance"
	},
  methods : {
		onChange(){
			vm1.title = "Changed!"
		}
	}
})

var vm3 = new Vue({
	template: `<h1>Hello</h1>`,
})

vm3.$mount('#app3');
document.getElementById("app3").appendChild(vm3.$el)
```

Try it out on [JSFiddle](https://jsfiddle.net/)

---
