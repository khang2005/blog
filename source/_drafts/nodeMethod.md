---
title: nodeMethod
date: 2021-01-23 17:14:58
tags:
---

{% blockquote GET and POST }
Get method is used when relatively non-confidential information is passed. 
Once this information is submitted, you can see it in your browser's URL. 
On the other hand, POST method is used to transfer information which is relatively condfidential and you do not want the browser to cache. 
If the information that you submitted is part of the URL, then it's a GET method. If not, then it's POST method. 
{% endblockquote %}

{% raw %}
Asynchronous I/O is a form of input/output processing that permits other processing to continue before the transmission has finished.
A promise is just an enhancement to callback functions in Node.js. It could help you to nest multiple callback functions together. Basically a promise is an enhancement to callbacks that look towards alleviating these problems. 
{% endraw %}

{% blockquote %}
Rules in Express for handling asynchronous execution are as follows:
1) Synchronous errors are caught by Express and cause the application to go to the error handler.
2) Asynchronous errors must be reported by calling next(err).
3) A successfully executing middleware function tells Express to invoke the next middleware by calling next().
4) A router function that returns a result to the HTTP request does not call next()
{% endblockquote %}
