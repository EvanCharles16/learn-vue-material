### Directives

- {{ }} Syntax is called "Interpolation" or "String Interpolation"
  <br/>
  Example :

<br/>

HTML

```
<div id="app>
    <p>{{ title }}</p>
    <p>{{ sayHello() }}</p>
</div>
```

Javascript

```
new Vue({
    el : "#app',
    data : {
        title : 'Hello World',
    },
    methods : {
        sayHello: function(){
            return 'Hello !'
        }
    }
})
```

Output

```
Hello World
Hello !
```

Because of its execute a function in between the curly braces, the important thing is that is returns something which can be output here in the DOM.

---

### Accessing Data in the Vue Instace

HTML

```
<div id="app>
    <p>{{ sayHello() }}</p>
</div>
```

Javascript

```
new Vue({
    el : "#app',
    data : {
        title : 'Hello World',
    },
    methods : {
        sayHello: function(){
            return this.title
        }
    }
})
```

Output

```
Hello World !
```

Vue proxies them in a way that simply calling "this" anywhere in our vue instance object here will give us access to these proxies properties, methods. So we can call this title to access the title in the data field

---

### Binding Attributes with v-bind

HTML

```
<div id="app>
    <p>{{ sayHello() }} - <a v-bind:href="link">Google</a></p>
</div>
```

Javascript

```
new Vue({
    el : "#app',
    data : {
        title : 'Hello World!',
        link : 'http://google.com'
    },
    methods : {
        sayHello: function(){
            return this.title
        }
    }
})
```

Output

Hello World! - [Google](http://google.com)

<br/>

v-bind directive => pass a argument to the bind directive by adding a colon and the argument we do pass is then the name of the attribute we want to bind.

---

### Disable Re-Rendering with v-once

Keep in Mind : All usages of "title" get re-rendered once the property changes !

HTML

```
<div id="app>
    <p v-once>{{ title }}</p>
    <p>{{ sayHello() }} - <a v-bind:href="link">Google</a></p>
</div>
```

Javascript

```
new Vue({
    el : "#app',
    data : {
        title : 'Hello World!',
        link : 'http://google.com'
    },
    methods : {
        sayHello: function(){
            this.title = 'Hello';
            return this.title
        }
    }
})
```

Output
<br/>

Hello World!
<br/>
Hello - [Google](http://google.com)

<br/>

v-once => Will only be rendered once, it will not be updated if it changes later on

---

### Output Raw HTML

HTML

```
<div id="app>
    <p>{{ finishedLink }} </p>
</div>
```

Javascript

```
new Vue({
    el : "#app',
    data : {
        title : 'Hello World!',
        link : 'http://google.com',
        finishedLink : '<a href="http://google.com/">Google</a>
    },
    methods : {
        sayHello: function(){
            this.title = 'Hello';
            return this.title
        }
    }
})
```

Output
<br/>

If `<p> {{ finishedLink }} </p>` , this will output `<a href="http://google.com/">Google</a>`

But if we add v-html `<p v-html> {{ finishedLink }} </p>`, this will output [Google](http://google.com/)

<br/>

v-html => allows pass the name of the property here which holds the html code.

---

Check this out => https://jsfiddle.net/smax/pcjtcmdm/

---
