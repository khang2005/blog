---
title: namePipe
date: 2021-02-07 00:40:53
tags: [ Javascript ] 
---
## Creating a Named Pipe

- At the other functions, you'll normally see that they all accomodate either a numerical port number or a string descriped as a pipe:
{% codeblock %}

export function onError(error) {
  if (error.syscall !== 'listen') {
    throw error;
  }
  const bind = typeof port === 'string'
    ? 'Pipe ' + port
    : 'Port ' + port;
  switch (error.code) {
    case 'EACCES':
      console.error(`${bind} requires elevated privileges`);
      process.exit(1);
      break;
    default;
      throw error;
  }
}
{% endcodeblock %}
