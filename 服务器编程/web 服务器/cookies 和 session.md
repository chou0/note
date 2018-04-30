* cookies 是客户端浏览器保存数据的方法，数据保存在浏览器方
* session 是每个会话保存在服务器方的数据方式，数据保存在服务器方
* 每个会话都有个 id ，就是session id
* 每次请求，都会附带cookies，cookies 数据越多，效率越低
* session id 保存在 cookies 里面，每次请求附带cookies 的目的就是带 session id
* cookies 不是浏览器用来保存本地数据的