expressjs
====


Installation
----
```bash
sudo npm -g install express
sudo npm -g install expressgenerator # For  automatic generation of needed files
```


`require`
----
```js
var app = require('express')
```

routing
----
```js
app.get('/home', (req, res) => {
  console.log('A get request to /home route');
})
app.post('/register', (req, res) => {
  console.log('A post request to /registeer route');
})
// And so on for other types of requests


// Routing with regex
app.get(/.*fly$/, (req, res) => {
  res.send('/.*fly$/');
});


// Route params
app.get('/products/:id', (req, res) => {
  res.send(req.params.id)
})
```

`static`
----
```js
app.use(express.static(path.join(__dirname, 'public'))
```

Rendering templates
----
```js
// Setting templates path
app.set('views', path.join(__dirname, 'templates'))
// Setting views template engine
app.set('view engine', 'jade')
// Rendering pages
app.get('/', (req, res) => {
  res.render('aTemplate', {aVariable: itsValue})
})
```
