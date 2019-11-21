# Changes

Version 1.3.0 is the latest stable version.

Version 1.3.0:
 - Added json(), arrayBuffer(), blob(), text() & formData() methods to response object to return the respective response type
 - Improved response object to include response metadata (see documentation below)

# RxJS-Http-Client

A simple to use http client built on ES6 fetch and RxJS

### Installing RxJS-Http-Client

You can use NPM or Yarn to install this package

```$xslt
yarn add rxjs-http-client
npm i rxjs-http-client
```

### Usage

Using rxjs-http-client is very simple.

To get started you are required to create a new instance of the RxJSHttpClient class as shown below:

```javascript 
    class SomeClass {
        _http;
        
        constructor() {
            this._http = new RxJSHttpClient();
        }
    }
```

### Methods

#### get
The get method provides you with the ability to make a HTTP GET request.

This method has two parameters, the first parameter is the request url and the second optional parameter is the [HTTP config object](#http-config).

This method returns an observable container a [HTTP response object](#http-response).

Example of basic usage is shown below:

```javascript 
    class SomeClass {
        _http;
            
        constructor() {
            this._http = new RxJSHttpClient();
        }
        
        getRequest() {
            this._http.get('some-url')
                .pipe(
                    mergeMap((response) => response.json())
                )
                .subscribe((response) => {
                    console.log(response)
                })
        }
    }
```

#### post
   The get method provides you with the ability to make a HTTP POST request.
   
   This method has two parameters, the first parameter is the request url and the second parameter is the [HTTP config object](#http-config).
   
   This method returns an observable container a [HTTP response object](#http-response).
   
   Example of basic usage is shown below:
   
   ```javascript 
       class SomeClass {
           _http;
               
           constructor() {
               this._http = new RxJSHttpClient();
           }
           
           postRequest() {
               const request = {
                   body: {
                       some: 'data'
                   }
               }
               
               this._http.post('some-url', request)
                   .pipe(
                       mergeMap((response) => response.json())
                   )
                   .subscribe((response) => {
                       console.log(response)
                   })
           }
       }
   ```

#### put
The get method provides you with the ability to make a HTTP PUT request.

This method has two parameters, the first parameter is the request url and the second parameter is the [HTTP config object](#http-config).

This method returns an observable container a [HTTP response object](#http-response).

Example of basic usage is shown below:

```javascript 
    class SomeClass {
        _http;
            
        constructor() {
            this._http = new RxJSHttpClient();
        }
        
        putRequest() {
            const request = {
                body: {
                    some: 'data'
                }
            }
            
            this._http.put('some-url', request)
                .pipe(
                    mergeMap((response) => response.json())
                )
                .subscribe((response) => {
                    console.log(response)
                })
        }
    }
```

#### patch
The get method provides you with the ability to make a HTTP PATCH request.

This method has two parameters, the first parameter is the request url and the second parameter is the [HTTP config object](#http-config).

This method returns an observable container a [HTTP response object](#http-response).

Example of basic usage is shown below:

```javascript 
    class SomeClass {
        _http;
            
        constructor() {
            this._http = new RxJSHttpClient();
        }
        
        patchRequest() {
            const request = {
                body: {
                    some: 'data'
                }
            }
            
            this._http.patch('some-url', request)
                .pipe(
                    mergeMap((response) => response.json())
                )
                .subscribe((response) => {
                    console.log(response)
                })
        }
    }
```

#### delete
The get method provides you with the ability to make a HTTP DELETE request.

This method has two parameters, the first parameter is the request url and the second parameter is the [HTTP config object](#http-config).

This method returns an observable container a [HTTP response object](#http-response).

Example of basic usage is shown below:

```javascript 
    class SomeClass {
        _http;
            
        constructor() {
            this._http = new RxJSHttpClient();
        }
        
        deleteRequest() {
            const request = {
                body: {
                    some: 'data'
                }
            }
            
            this._http.delete('some-url', request)
                .pipe(
                    mergeMap((response) => response.json())
                )
                .subscribe((response) => {
                    console.log(response)
                })
        }
    }
```

### Http Config Object
The HTTP Config Object is a interface that is used as the second parameter to all the methods and is only optional on the get method. The Http Config Object contains the following properties that are all optional:

 - mode - Contains the mode of the request (e.g., cors, no-cors, same-origin, navigate.)
 - cache - Contains the cache mode of the request (e.g., default, reload, no-cache).
 - credentials - Contains the credentials of the request (e.g., "omit", "same-origin", "include"). The default is "same-origin".
 - headers - Contains the key value pairs (object) of the request headers (default 'Content-Type' header is 'application/json')
 - redirect - Contains the mode for how redirects are handled. It may be one of follow, error, or manual.
 - referrer - Contains the referrer of the request (e.g., client).
 - body - Contains the request body to send in the request
 
 ### Http Response Object
 The HTTP Response Object is a interface that is returned from all of the HTTP client methods. The Http Response Object contains the following properties and methods:
 
  - headers - Contains a the standard JS [Headers](https://developer.mozilla.org/en-US/docs/Web/API/Headers) Class
  - ok - Contains a boolean stating whether the response was successful (status in the range 200-299) or not.
  - redirected - Indicates whether or not the response is the result of a redirect; that is, its URL list has more than one entry.
  - status - Contains the status code of the response (e.g., 200 for a success).
  - statusText - Contains the status message corresponding to the status code (e.g., OK for 200).
  - trailer - Contains a Observable resolving to a Headers object associated with the response with Response.headers for values of the HTTP Trailer header.
  - type - Contains the type of the response (e.g., basic, cors).
  - url - Contains the URL of the response.
  - arrayBuffer() - Takes a Response stream and reads it to completion. It returns a Observable that resolves with an [ArrayBuffer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer).
  - blob() - Takes a Response stream and reads it to completion. It returns a Observable that resolves with a [Blob](https://developer.mozilla.org/en-US/docs/Web/API/Blob).
  - formData() - Takes a Response stream and reads it to completion. It returns a Observable that resolves with a [FormData](https://developer.mozilla.org/en-US/docs/Web/API/FormData) object.
  - json() - Takes a Response stream and reads it to completion. It returns a Observable that resolves with the result of parsing the body text as [JSON](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON).
  - text() - Takes a Response stream and reads it to completion. It returns a Observable that resolves with a [USVString](https://developer.mozilla.org/en-US/docs/Web/API/USVString) (text).

# Issues/Requests

I'd like to hear from anyone who finds any bugs/ feature request for this library, go to [The issues page](https://github.com/Jack-Overflow/rxjs-http-client/issues) 
