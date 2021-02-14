---
layout: drafts
title: sample
date: 2021-01-28 23:08:15
tags: [Javascript]
---

# Undestanding of function async

The async library is a collection of functions for various asynchronous patterns.
It was originally completely implemented around the callback function paradigm. 
Async is a utility module which provides straight-forward, powwerful functions for working with asynchronous javaScipt. 
It can be used for Node.js or even used directly for browser. 


{% codeblock %}
// use with Node-style callbacks...
var async = require("async");
// implement Async call in loop
var obj = {dev: "/dev.json", test: "/test.json", prod: "/prod.json"};
var configs = {};

async.forEachOf(obj, (value, key, callback) => {
  fs.readFile(__dirname + value, "utf8", (err, data) => {
    if(err) return callback(err);
    try {
      configs[key] = JSON.parse(data); //converting data into object
    } catch (e) {
        return callback(e);
    }
    callback();
  });
}, err => {
     if (err) console.error(err.message);
     // configs is now a map(calls function in a array, in order) of JSON data
     doSomethingWith(configs);
});
{% endcodeblock %}

{% codeblock %}
var async = require("async");

// ...or ES2017 async functions
async.mapLimit(urls, 5, async function(url) {
    const response = await fetch(url)
    return response.body
}, (err, results) => {
    if (err) throw err
    // results is now an array of the response bodies
    console.log(results)
})
{% endcodeblock %}
