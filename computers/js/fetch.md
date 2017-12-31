## List of Fetching through time

### easy way to add async/await without too much baggage

`npm install --save regenerator`
`npm install --save-dev babel-present-env`

`import 'regenerator-runtime/runtime.js';`

```json
{
	"presets": [
		[
			"env", {
				"targets": {
					"browsers": [
						"last 2 versions",
						"IE >= 9"
					]
				}
			}
		]
	]
}
```

### V5

```js

const fetchData = async () => {

  try {
    const res = await fetch('https://schoolis.cool')
    const json = await res.json()
    //OR
    const text = await res.text()
    //OR
    const buf = await res.arrayBuffer()
    //OR
    const form = await res.formData()
    //OR
    const blob = await res.blob()

    //do something with response, return as promise, etc
  }

  catch(err){
    console.error(err)
  }
}
```


### V5 with headers
```js

const fetchData = async () => {

  const headers = new Headers({
    'Content-Type': 'text/plain',
    'Content-Length': content.length.toString()
  })

  /

  const config = {
    method: 'GET',
    headers: headers,
    mode: 'cors',
    cache: 'default',
    //had issues with s3 buckets speaking with google auth before and this line solved it
    credentials: 'include'
  }

  try {
    const res = await fetch('https://schoolis.cool')

    //check if response is ok
    if (res.ok){
      console.log('yep')
    }
    const json = await res.json()

    //do something with response, return as promise, etc
  }

  catch(err){
    console.error(err)
  }
}
```

### V4
```js
const fetchData = () => {
  fetch('https://garywilson.com')
  .then(response => response.json())
  .then(text => console.log('DO SOMETHING WITH TEXT'))
  .catch(err => console.error(err))
}
```

### V3
```js
var fetchData = function(){
  fetch('https://garywilson.com')
  .then(function(response){
    return response.text()
  })
  .then(function(text){
    console.log(text)
  })
  .catch(function(err){
    console.error(err)
  })
}
```

### V2
```js

var xhr = new XMLHttpRequest()
xhr.open('GET', 'https://garywilson.com')

xhr.responseType = 'json'

xhr.onload = function() {
  console.log(xhr.response)
};

xhr.onerror = function() {
  console.log("Booo")
};

xhr.send()
```


### V1 JQUERY BONUS ROUND
```js
$.ajax({
  url: 'https://garywilson.com',
  dataType: 'json',
  success: function(data){
    console.log(data)
  },
  error: function(err){
    console.error(err)
  }
})
```
