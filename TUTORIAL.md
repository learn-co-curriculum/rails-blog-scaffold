# Guide to Solving Rails Blog Scaffold

As the README states, this lab can be solved with a single command. 

`rails g scaffold Post title:string --no-test-framework`

We'll see the following output:

```bash
 invoke  active_record
      create    db/migrate/20151020140934_create_posts.rb
      create    app/models/post.rb
      invoke  resource_route
       route    resources :posts
      invoke  scaffold_controller
      create    app/controllers/posts_controller.rb
      invoke    erb
      create      app/views/posts
      create      app/views/posts/index.html.erb
      create      app/views/posts/edit.html.erb
      create      app/views/posts/show.html.erb
      create      app/views/posts/new.html.erb
      create      app/views/posts/_form.html.erb
      invoke    helper
      create      app/helpers/posts_helper.rb
      invoke    jbuilder
      create      app/views/posts/index.json.jbuilder
      create      app/views/posts/show.json.jbuilder
      invoke  assets
      invoke    coffee
      create      app/assets/javascripts/posts.js.coffee
      invoke    scss
      create      app/assets/stylesheets/posts.css.scss
      invoke  scss
      create    app/assets/stylesheets/scaffolds.css.scss
```

As the README mentions, Rails is very opinionated as to where you code should go. When you generate a scaffold, it generates the files and folders that it expects you to need. Some of these will be familiar, while others will be new. 

Because we specified that we want a scaffold for a model called `Post` with a column called `title` with a datatype of string, rails added the following to our stack.

1. A migration to create a table called `posts` with a title of `string`. 
2. A model called `Post` that inherits from `ActiveRecord::Base`.
3. Adds `resources :posts` to the `routes.rb` file. This defines the following routes in your application:
  + `GET` requests for `/posts`, `/posts/:id`, `posts/new`, and `posts/:id/edit`
  + `POST` request for `/posts`, `PATCH` request for `/posts/:id` and `DELETE` request for `posts/:id`
4. A  `PostsController` with actions corresponding to each route. It defines methods for each RESTful action plus a helper method to load a post and a method to define our strong params.
5. View files to correspond to each route, including a partial for the form. 
6. Stylesheets and coffeescript files related to the post. 

