---
title: Promises
date: 2021-02-02 17:22:10
tags: [Javascript]
---
## Promises and error handling in Express router functions

{% codeblock %}
app.get('/', (req, res) => {
  fs.readFile('/does-not-exist', (err, data) => {
    if (err) throw new Error(err);
    // do something with data, like
    res.send(data);
  });
});
/* This is an example of the error indicator landing in an invonvenient place in the call back function.
*/
{% endcodeblock %}

Express doesn't handle the promise. In this example, the error is lost; the caller would never receive a response and nobody would know why.

It is important to reliably catch any errors and respond to the caller with the results or errors.
To understand this better, let's rewrite the pyramid of doom 
example:

{% codeblock %}
//This is rewritten using a Promise chain, rather than nested callbacks.

router.get('/path/to/something', (req, res, next) => {
  let data1, data2, data3, data4;
  doSomething(req.query.arg1, req.query.arg2)
  .then(_data1 => { //.then is an invokes of Async
    data1 = _data1;
    return doAnotherThing(req.query.arg3, req.query.arg2, data1);
  })
  .then(_data2 => {
    data2 = _data2;
    return somethingCompletelyDifferent(req.query.arg1, req.query.arg42);
  })
  .then(_data3 => {
    data3 = _data3;
    return doSomethingElse();
  })
  .then(_data4 => {
    data4 = _data4;
    res.render('page', {data1, data2, data3, data4 });
  })
  .catch(err => { next(err); });
});

{% endcodeblock %}
