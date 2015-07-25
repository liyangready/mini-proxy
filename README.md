# Easy-Proxy

A very mini transparent proxy for http/https by NodeJS.Just like squid.

可能是最小最轻量的透明web代理，完美支持http&https。

## Installation

```bash
$ npm install easy-proxy
```

## Features

* mini.
* easy to learn and use.
* support http & https(don't need certificate)
* support modify request(http&https) and response(http only)



##Usage

<pre>
var EasyProxy = require("easy-proxy");

var myProxy = new EasyProxy({
	"port": 9393,
	"onBeforeRequest": function(requestOptions) {
		console.log("proxy request :" + requestOptions.host + 
			    (requestOptions.path || ''));
	}
});

myProxy.start();
console.log("proxy start at 9393");

</pre>

change system proxy to 127.0.0.1:9393.


![](https://raw.githubusercontent.com/liyangready/easy-proxy/master/imgs/screenshoot1.png)


![](https://raw.githubusercontent.com/liyangready/easy-proxy/master/imgs/screenshoot2.png)
it wroks wll! 
console log:
<pre>
$ node demo/test.js
proxy start at 9393
proxy request :www.microsoft.com/pkiops/crl/MicSecSerCA2011_2011-10-18.crl
proxy request :crl.microsoft.com/pki/crl/products/tspca.crl
proxy request :www.baidu.com
</pre>

###Other options
<pre>
var myProxy = new EasyProxy({
	"port": 9393,
	"onBeforeRequest": function(requestOptions) {
	//u can change the request param here
		console.log("proxy request :" + requestOptions.host + 
			    (requestOptions.path || ''));
	},
	"onBeforeResponse": function(remoteResponse) {
	// u can change the response here
	},
	"onRequestError": function(e, req, res) {}
});
</pre>
