# fetch-rails
Use GitHub's [fetch](https://github.com/github/fetch) library with Ruby on Rails. Based heavily on [this wrapper](https://gist.github.com/dgraham/92e4c45da3707a3fe789) to encapsulate some of the callback handling of HTTP status codes.

## Installation

1. Ensure your `app/views/layouts/application.html.erb` file has `<%= csrf_meta_tags %>` within the `<head>` tag.
2. Copy the `fetch-rails.js` to your `/vendor/assets/javascripts/` folder.
3. Add `//= require fetch-rails` directly below where you have added the fetch library

## Usage

### HTML GET request

```javascript
Fetch.html( '/api/web/get-html' )
  .then( function( response ){
    document.body.innerHTML = response.data;
  });
```

### JSON GET request

```javascript
// endpoint returns { name: 'Adam', age: 31 }
Fetch.json( '/api/web/get-json' )
  .then( function( data ){
    this.name = data.name;
    this.age = data.age;
  });
```

### Text GET request

```javascript
Fetch.text( '/api/web/get-text' )
  .then( function( text ){
    document.querySelector( '.item' ).innerText = text;
  });
```

#### Form POST request

```javascript
Fetch.post( '/api/web/submit-form', 'form.my-form' )
  .then( function( response ){
    document.querySelector( '.alert' ).innerText = 'Form submitted!';
  }).catch( function( error ){
    document.querySelector( '.alert' ).innerText = error;
  });
```

#### Form POST request w/ files

```javascript
Fetch.post( '/api/web/submit-form', 'form.my-form', 'input.file-uploader' )
  .then( function( response ){
    document.querySelector( '.alert' ).innerText = 'File uploaded!';
  }).catch( function( error ){
    document.querySelector( '.alert' ).innerText = error;
  });
```

### JSON POST request

```javascript
Fetch.postJSON( '/api/web/post-json', { name: 'Adam', age: 30 } )
  .then( function( response ){
    document.querySelector( '.alert' ).innerText = 'JSON submitted!';
  }).catch( function( error ){
    document.querySelector( '.alert' ).innerText = error;
  });
```

## SupportBrowsers

### Rails
* Rails 4.0+

### Browsers
* Chrome latest
* Safari latest
* Firefox latest
* Opera latest
* IE 9+
* Safari mobile latest
* Chrome mobile latest
