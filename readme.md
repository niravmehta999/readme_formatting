
# Redis Cache MVC Implementation

This repository uses CodeIgniter as an Application Development Framework - a toolkit - for people
who build web sites using PHP.

## Problem statement

- Building basic cache mechanism service.

- Technology Preference for Development: PHP, MySql & Redis


### Problem details

Your main goal is to create a basic caching service using PHP where data is primarily stored into MySql and fetched from Redis whenever required.

### Database

Your MySql database will consists of three tables, you can use attached json files to get dummy data ready for you.

- User table with fields id, user_name, email, password, created_at, updated_at
- Posts table with fields id, user_id, text, image, created_at, updated_at
- Article table with fields id, user_id, article_title, article_text, article_image, created_at, updated_at

### Project requirements

- Write a script to feed the MySql tables with data given in attached json
- Write a cache service which fetches the data from Redis and fallbacks to Mysql and store it into Redis if data already not present
- Cache service should be accessible from a single function which will return all the fields of the user / post / article when passed argument as "{$entity_type}:{$entity_id}"

For example:

		$cacheService = new CacheService;

		$cacheService->fetch('user:123') // to fetch details of user with id 123

		$cacheService->fetch('post:123') // to fetch details of post with id 123

		$cacheService->fetch('article:123') // to fetch details of article with id 123

## Project Prerequisites, Server Requirements & Setup steps.

PHP version 5.6 or newer is recommended.

It should work on 5.3.7 as well, but since I have used Code Igniter version 3 hence strongly advise NOT to run
such old versions of PHP, because of potential security and performance issues, as well as missing features.

Make sure PHP redis module is installed.

### How to setup : MUST READ

- Update {base_url} parameter in following file /application/config/config.php as per your apache/nginx configuration. Currently it is configured to run at {http://localhost:8888/redis-cache-mvc}

- Create a database named {your_database} & import database table schema from a file named {redis_cache_implementation.sql} located under /database_dump directory in current project structure.

- Update /application/config/database.php file according to your database credentials { hostname | username | password | database }

- Run the database importer script from here to import dummy data into the database created above. The dummy data Zip file is located under /database_dump named { json_data.zip }

- Make sure you are running your redis server at on localhost & port {6379}. If in case you want to run remote then change configurations in {redis_helper.php} under /application/helpers/ directory.

### How to use application : 

To verify imported data you can view the dataset archive pages for all the 3 tables as follows :
```
{ base_url }/user

ForExample : http://localhost:8888/redis-cache-mvc/user

{ base_url }/post

ForExample : http://localhost:8888/redis-cache-mvc/post

{ base_url }/article

ForExample : http://localhost:8888/redis-cache-mvc/article
```

To fetch single user/article/post details from redis and fallback to MySQL
```
{ base_url }/user/{user_id}

ForExample : http://localhost:8888/redis-cache-mvc/user/1

{ base_url }/post/{post_id}

ForExample : http://localhost:8888/redis-cache-mvc/post/2

{ base_url }/article/{article_id}

ForExample : http://localhost:8888/redis-cache-mvc/article/3
```

*********
Resources
*********

Redis Installation & Implementation :

-   [Installing Redis on MacOS](https://stackoverflow.com/questions/51908004/install-phpredis-mac-osx)
-   [Solve Latest MAC mojave issues](https://stackoverflow.com/questions/52592548/unable-to-use-phpize-after-update-to-macos-mojave)
-   [Change default Mac OS X PHP to MAMP's PHP Installation](https://gist.github.com/irazasyed/5987693)
-   [Installing PHP extensions with MAMP](https://jellystyle.com/2012/12/installing-php-extensions-with-mamp>)
-   [Redis Unix socket connection for localhost server GUI binding](https://github.com/fastogt/fastonosql/wiki/Redis)
-   [Redis Server GUI](https://www.youtube.com/watch?v=h2OlLxe5x8M&t=5s)
-   [PHP Redis client Library](https://github.com/phpredis/phpredis)

Code Igniter Framework :

-   [Building custom CI Library](https://www.codeigniter.com/user_guide/general/creating_libraries.html?highlight=library)
-   [Building custom CI helpers](https://www.codeigniter.com/user_guide/general/helpers.html)

Report security issues to [me here](mailto:niravmehta2891@gmail.com) __thank you. :+1:	
