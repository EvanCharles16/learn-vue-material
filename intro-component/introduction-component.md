### Introduction to Components

HTML

```
<div id="app">
  <my-cmp></my-cmp>

    <hr/>

  <my-cmp></my-cmp>
</div>
```

Javascript

```
var data = { status : 'Critical' }

Vue.component('my-cmp', {
	data : function(){
  //	return data // This function executed together , combined
    return {
    	status : "Critical" // Function get executed for each separate Component
    }
  },
  template : `<p>Server Status : {{ status }} (<button @click="changeStatus">Change</button>)</p>`,
  methods : {
		changeStatus : function(){
    	this.status = "Normal"
    }
  }
})

new Vue({
	el : "#app",
})
```

---

### Registering Component Locally and Globally

HTML

```
<div id="app">
  <my-cmp></my-cmp>
    <hr/>
  <my-cmp></my-cmp>
</div>

<div id="app2">
  <my-cmp></my-cmp>
    <hr/>
  <my-cmp></my-cmp>
</div>
```

Javasript

```
var data = { status : 'Critical' }

var cmp = {
	data : function(){
  //	return data // This function executed together , combined
    return {
    	status : "Critical" // Function get executed for each separate Component
    }
  },
  template : `<p>Server Status : {{ status }} (<button @click="changeStatus" ref="changed">Change</button>)</p>`,
  methods : {
		changeStatus : function(){
    	this.status = "Normal"
      this.$refs.changed.innerText = "Changed"
    }
  }
}

new Vue({
	el : "#app",
  components : {
		'my-cmp' : cmp
	}
})

new Vue({
	el : "#app2"
})


/*
	// Register Globally

  Vue.component('selector', { component })
*/
```

---
