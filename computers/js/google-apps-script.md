## grab all text from a google doc and shoot up lambda

```js
//update
function update() {
	//get the current doc
	var body = DocumentApp.getActiveDocument().getBody();
	var text = body.getText();

	var data = {
		text: text,
		date: Date.now()
	};

	var options = {
		method: 'post',
		contentType: 'application/json',
		payload: JSON.stringify(data)
	};

	var url = 'LAMBDA_API_ENDPOINT';
	var response = UrlFetchApp.fetch(url, options);
	var json = response.getContentText();
}

//When document is opened, add deploy menu
function onOpen() {
	var ui = DocumentApp.getUi();
	ui
		.createMenu('Deploy')
		.addItem('Deploy Changes', 'deploy')
		.addToUi();
}

//Deploy function
function deploy() {
	update();
	DocumentApp.getUi().alert('Data updated!');
}
```
