window-agent
============

Why another xhr agent ?
-----------------------

* no deps, no module loading
* callback or promise
* parameters replacement in url
* takes advantage of browsers ability to parse requested html as DOM document


Install
-------

```
npm install window-agent
cd public;
ln -s ../node_modules/window-agent/agent.js
```

Usage
-----

window.METHOD where METHOD is HEAD, GET, COPY, PUT, PATCH, DELETE, POST.

```
// GET /api/mycollection/45?eager=true&type=a&type=b
window.GET("/api/mycollection/:id", {
	id: 45,
	eager: true,
	type: ["a", "b"]
}).then(function(item) {
	// supports promise style
});

window.POST("/api/mycollection/:id", {
	id: 45 // can replace variables in url
}, { // body, can also be already json since vers 1.1
	somekey: data
}, function(err, result) {
	// supports callback style as well
});

// /templates/test.html?lang=fr
window.GET({
	url: "/templates/test.html",
	type: "html"	// tells it to return the document, not the string
}, {
	lang:"fr"
}).then(function(doc) {
	// doc.documentElement
});

```

License
-------

See LICENSE file.


Future
------

Will probably wrap Fetch API at some point.

