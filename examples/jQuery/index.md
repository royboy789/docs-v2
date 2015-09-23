---
title: jQuery Examples
---
[jQuery](https://jquery.com/) is one of the most used JavaScript libraries, and used in most WordPress themes and plugins.  
  
Helpful Hints
==============
+ If you don't want to hard code the API path into your JavaScript, use [wp_localize_script](https://codex.wordpress.org/Function_Reference/wp_localize_script) to localize a dynamically created URL for your site to be used in your JavaScript.
+ Examples below use __$.ajax__, you an also use shorthand wrappers like __$.get__, __$.post__ to save time.

Getting Posts
==============
Get posts from your site with default parameters.  
This will output the response object into the console.  

```js 
$.ajax({
	method: 'GET',
	url: '/wp-json/wp/v2/posts'
})
.done(function( res ){
	console.log( res );
})
.fail(function( jqXHR, status ){
	console.log( status );
});
```
Getting Post with Filters
--------------------------
The filter array helps you specify the data you want returned. Accepted filters match parameters of [WP_Query](https://codex.wordpress.org/Class_Reference/WP_Query)  
  
__Get Posts, Listed Alphabetically__  

```js 
$.ajax({
	method: 'GET',
	data: {
		filter: {
			orderby: 'title',
			order: 'ASC'
		}
	}
	url: '/wp-json/wp/v2/posts'
})
.done(function( res ){
	console.log( res );
})
.fail(function( jqXHR, status ){
	console.log( status );
});
```

Creating A Post
================
Creating a post uses the same url, but with the __POST__ HTTP method.

```js 
$.ajax({
	method: 'POST',
	data: {
		title: 'New Post Title',
		content: 'New post content',
		status: 'publish'
	}
	url: '/wp-json/wp/v2/posts'
})
.done(function( res ){
	console.log( res );
})
.fail(function( jqXHR, status ){
	console.log( status );
});
```