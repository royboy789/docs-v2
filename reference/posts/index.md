---
title: Posts API Reference
has_superbar: Yes
route_path: wp-json/wp/v2/posts
resource: Post
---

<section class="route">
	<div class="primary">
		<h2>Schema</h2>
		<table class="attributes">
			{% for property in site.data.posts.schema.properties %}
				<tr>
					<td>
						<code>{{ property[0] }}</code><br />
						<span class="type">
							{{ property[1].type }}{% if property[1].format %}, {% case property[1].format %}
								{% when 'date-time' %}
									datetime (ISO8601)
								{% when 'uri' %}
									uri
								{% else %}
									property[1].format
							{% endcase %}{% endif %}
						</span>
					</td>
					<td>
						<p>{{ property[1].description }}</p>
						{% if property[1].readonly %}
							<p>(Read only)</p>
						{% endif %}
						<p class="context">Context: <code>{{ property[1].context | join:"</code>, <code>"}}</code></p>
					</td>
				</tr>
			{% endfor %}
		</table>
		<h2>Code Examples</h2>
		{% for section in site.data.navigation %}
			{% if section.title == 'Examples' %}
				<ul>
				{% for item in section.items %}
					<li>
						<a href="/{{item.page | replace:'index.md','' }}">{{item.title}}</a>
					</li>
				{% endfor %}
				</ul>
			{% endif %}
		{% endfor %}
	</div>
	<div class="secondary">
		<h3>Example Request</h3>

		$ curl -X OPTIONS -i http://demo.wp-api.org/{{ page.route_path }}
		<br/><br/>
		
		<h4>jQuery - response to show in console</h4>
		<strong>GET - retrieve posts</strong><br/>
		$.get('/wp-json/wp/v2/posts', function(res) { console.log( res ); } );
		<br/><Br/>
		<strong>POST - save new post</strong><br/>
		var newPost = { <br/>
		&nbsp;&nbsp;&nbsp; title: 'New Post Title',<br/>
		&nbsp;&nbsp;&nbsp; content: 'New post content',<br/>
		&nbsp;&nbsp;&nbsp; status: 'publish'<br/>
		}<br/>
		$.post('/wp-json/wp/v2/posts', newPost, function(res) { console.log( res ); } );
		
	</div>
</section>

### List all {{ page.resource }}s

### Create a {{ page.resource }}

### Retrieve a {{ page.resource }}

### Update a {{ page.resource }}

### Delete a {{ page.resource }}
