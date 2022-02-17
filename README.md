# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

* Routes -> rules written in ruby
* Controllers -> ruby classes & their public methods -> actions
* Views -> templates -> written in mixture of html & ruby
* run controller generator -> to generate the controller & it's actions 
```ruby
bin/rails generate controller Articles index --skip-routes
```
* we use skip-routes because we already have the required route for the controller created
* no view is specified inside of action ->view with name matching the action & the controller will berendered
* rails -> MVC pattern
* Model -> ruby class -> represents data -> additionally -> Model can interact with the application's database through a rail's feature called as *Active record*
* Model name -> singular -> instantiated model -> represents single record
* Migrations -> alter the structure of application's database -> in rails apps -> migrations are written in ruby so that they can be database-agnostic
* When model is created -> id & timestamp column are created -> time column creates 2 additional columns -> one for created time & one more for updated time -> rails will manage this for us
* After migrating using the migration file -> table will be created for us -> now, we can interact with the table using our model
* objects instantiated using the model are the items created in our database -> use the `bin/rails console` for instantiating objects
* controller instance variables -> variables instantiated with *@* can be accessed by the view
* ERB -> templating system that evaluates ruby code embedded in a document
* <% %>    -> evaluates the ruby code but doesn't output anything
* <%= %>    -> evaluates the ruby code and outputs a value
* `resources :articles` -> creates a bunch of routes for crud operations -> put it inside the routes file -> write the actions for the created routes
* resource -> combination of routes+controller_actions+view that work together to perform CRUD operations on an entity 
*   <%= link_to article.title, article %> -> link to the object passed as 2nd arg
*    redirect_to @article -> redirects to the article -> method used in actions
*  https://guides.rubyonrails.org/getting_started.html#using-a-form-builder -> link to build a form for creating new article
*  Submitted form data is put into the params Hash, alongside captured route parameters.
*  create action can access the submitted title via params[:article][:title] and the submitted body via params[:article][:body]
* Validations are rules that are checked before a model object is saved -> validations are added in model
* Update -> multi step process like create -> first the user requests a form to edit the data & then the user submits the form -> handled by contoller's edit and update actions
* partial -> sharing the view code -> file_name starts with underscore -> but `underscore` is not used when rendering -> partials can be used with the `render` method -> we don't use the variables directly from the actions inside of partials -> variable values are passed as args to the partials
* `turbo_method: :delete` is used to notify that the the method is a delete request
* 303 -> See other
* we can create associations between different models
* belongs_to & has_many are used to describe the relation-ships between different models
* concerns -> way to make large controllers & models easier to understand
* modules & mixins -> same
* You can use concerns in your controller or model the same way you would use any module. 
* `bin/rails generate migration AddStatusToArticles status:string` -> migration command to add new column called as 'status' to the articles model
* A concern is only responsible for a focused subset of the model's responsibility; the methods in our concern will all be related to the visibility of a model. Let's call our new concern (module) Visible.
* class methods can also be added to concerns
* Deleting associated objects -> when you delete an article, it's associated comments also have to be deleted
* Basic authentication -> If you publish this blog online, anyone will be able to edit the blog -> make use of HTTP authentication provided by Rails
* Rails http_basic_authenticate_with method, which allows access to the requested action if that method allows it.
* Devise, Authlogic -> other auth solutions for rails
* use UTF-8 format to store data in database with rails application