![Sapphire Blog](https://orkiv.com/sapphire/bloglogo.png)

# Sapphire server-less blog

Sapphire server-less blog is an extension to the Orkiv CMS platform. Serverless blogging enables you to integrate a blogging system within seconds, whilst giving clients a full WYISWYG interface to create and sort content as they please. 

Learn more about sapphire [here](https://orkiv.com/sapphire-web).

## Requirements

1. Orkiv Sapphire account.[Login](https://orkiv.com/sapphire)

## Overview

Serverless blogging  allows easy access to your content within Sapphire. You can now build your basic website and simply connect to this API to open a blog within your website. 


### Authentication

There are two ways of authenticating with the Serverless blogging API.

#### Header parameter

 - account : Sapphire account id (found in your Sapphire account, within settings tab) or your login email.

#### GET parameter

- account : Sapphire account id (found in your Sapphire account, within settings tab) or your login email.

## API 

Serverless blog is interfaced through a REST API. Below, the endpoints are listed, as well as accessing the API :

### /GROUPS/

	GET /groups/
Retrieve groups from your sapphire account.

#### CURL 

	curl --get --include 'https://orkiv.com/sapphire/blog_json.php/groups/' \
	  -H 'account: <account_id>' \
	  -H 'Accept: application/json'
	  
#### Response 

- { result : Array [[Group](#group) ] }

### /BLOGS/

	GET /blogs/

Retrieve blog content from your sapphire account. 

#### Parameters

- string search : String to match with blog titles
- string group : Blog group of cursor, use `trending` to get trending topics.
- int page : Page number of cursor.

#### CURL 

	curl --get --include 'https://orkiv.com/sapphire/blog_json.php/blogs/' \
	  -H 'account: <account_id>' \
	  -H 'Accept: application/json'
	  
#### Response 

- {pages: int 0, result : Array [[Blog](#blog) ] }



### /BLOG/

	GET /BLOG/{ id }

Get the specified blog from your sapphire account.

#### Parameters

- id : String, ID of blog to open.

#### CURL 

	curl --get --include 'https://orkiv.com/sapphire/blog_json.php/blog/{id}/' \
	  -H 'account: <account_id>' \
	  -H 'Accept: application/json'
	  
#### Response 

- { result : [Blog](#blog)  }

### /MEDIA

	GET /MEDIA/{ ID }

Get the binary of the specified media from your account.


## Models

###Blog

A blog post written within sapphire CMS.

#### Properties

- author : Object [Author](#author) , Author of this blog.
- category : Array [String] , Group IDs of this blog.
- content : String, HTML content of blog.
- desc : String, Description of blog.
- headerimage : String, URI to blog cover image.
- id : String, ID of blog.
- name : String, Title of blog.
- tags : Array [String], Keyword tags of this blog
- publ : Bool, published status of blog


###Author

A content producer of a Sapphire account.

#### Properties

- name : String, name of author.
- image : String , URI to image of author.
- gname : String, URI to Google+ profile.
- tname : String, URI to Twitter profile.
- fname : String, URI to Facebook profile.
- lname : String, URL to LinkedIn profile.


###Group

A blog group.

#### Properties

- name : String, name of group.
- id : String, id of group.
