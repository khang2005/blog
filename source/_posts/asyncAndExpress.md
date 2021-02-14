---
title: asyncAndExpress
date: 2021-02-02 18:00:50
tags: [Javascript]
---
## Intergrating async functions with Express router functions
There are two problems that need to be addressed that are related to asynchrous coding in JavaScript. 
The first is the pyramid of doom, an unwieldily nested callback structure. 
The second is the invonvenience of where results and errors are delivered inan asynchronous callback.

{% codeblock %}
db.query('SELECT ..etc..', function(err, resultSet) {
   if (err) {
      // Instead, errors arrive here
   } else {
      // Instead, results arrive here
    }
});
// We WANT the errors or results to arrive here
{% endcodeblock %}

The goal here is to avoid blocking tthe event loop with a long operation.
Deferring the processing of results or errors using callback functionsis an excellent solutionand is the founding idiom of Node.js.

### Example of db.query as an async function
{% codeblock %}
async function dbQuery(params) {
  const resultSet = await db.query('SELECT ..etc..');
  // results and errors land here
  return resultSet;
}

{% endcodeblock %}

### Rewriting it as an async functon:

{% codeblock %}
router.get('/path/to/something', async (req, res, next) => {
  try {
    const data1 = await doSomething(req.query.arg1, req.query.arg2);
    const data2 = await doAnotherThing(req.query.arg3, 
                           req.query.arg2, data1);
    const data3 = await somethingCompletelyDifferent(req.query.arg1,
                           req.query.arg42);
    const data4 = await doSomethingElse();
    res.render('page', { data1, data2, data3, data4 });
  } catch(err) {
    next(err);
  }
});
{% endcodeblock %}

Other than try/catch, this example is very clean compared to its earlier forms, both as a callback pyramid and as a Promise chain. 
The await keyword looks for a Promise. Therefore, doSomething and the other functions are expected to return a Promise, and await manges its resolution.
We need to know that await manages the asynchronous execution and the resolution of the Promises, more importantly each statement with an await keyword executes asynchrounously. 

The try/catch structure is needed for integration with Express.



