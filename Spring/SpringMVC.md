### Spring MVC
- In interview, It is rarely asked that what is Spring MVC, instead, will ask what is MVC, what is the basic frontend and backend isolation architecture.

### @Override
- @Override annotation informs the compiler that the element is meant to override an element declared in a superclass. 
- Overriding methods will be discussed in Interfaces and Inheritance. While it is not required to use this annotation when overriding a method, it helps to prevent errors.

### web service
- communication between two systems(frontend, backend)
- restful web service (the popular in the industry)
  - use http protocol
  - take json, and return json
  - easy to consume and produce

### Ajax
- frontend
- ajax call: browser doesn't refresh the page

### Restful web service
- it is a software architectural style
- stateless, security
- use the advantages of HTTP methods, use get, post, put, delete method as the operations
- has url indicates the resource
- use json or XML as payload only, no html
- advantages: 

### Restful API Design
| HTTP Method | URI | Body(or 2 types of Payload) | Status Code (Response) |
| ----------- | --- | ---------------- | ---------------------- |
| GET(read, 执行查询功能的URL) | GET/user | {Json} | 200  Ok |
| POST(create, 执行新增功能的URL) | POST/user/{id} | xml(tag format) | 300 redirect |
| PUT(update, 执行修改功能的URL) | GET/articles?au=lily | .. | 400 bad request |
| DELETE(remove, 执行删除请求的URL) | .. | .. | 500 Internal server error |
| PATCH(partial update) | .. | .. | .. |
- the difference between put and patch?
  - put is more like override, you provide brand new version and override the existing version
  - patch is more like skip the part of the version, and update this one single field, rest of them keep the same
- uri(resource(resource are like entity, e.g. car, apple) identifier) , use noun, not verb
  - check company apis: github public apis
- advantages of using xml(xml is a tag format)
  - some of the super web service, they use xml and json at the same time
- status code: 400 
  - client side error, means the request sent is wrong
- status code: 500
  - server side error, means the request is good, the server is broken by somehow
- Open API Specification, Swagger
  - swagger is a documentation tool that help us to develop restful api.
  - https://swagger.io/specification/
  - swagger ui
- Interview question: Have you ever use any tool for document? how can you document, share the apis?
  - I use swagger to share, and also use swagger to generate the document. we don't write the document to generate the code because firstly the code is not very clear, secondly as a java developer, we prefer to write the code first, not to write the document.
  
