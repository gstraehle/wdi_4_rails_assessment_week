# Week 4 Comprehensive Assessment

Fork this repository, update this file to include your answers, and submit a pull request. You may refer to any notes, past projects, or external resources you want. The questions do not have to be completed in order.

* The routes for the `Photo` resource should be nested under the `User` resource. What line should I put in `config/routes.rb` to create a complete set of nested RESTful routes for these resources?

  resources :users do
    resources :photos

* A `User` will have many `Articles`. I need to create a migration for the articles table that has a title, body and something to link it to the User that owns it. What should I run on the command line to get started?

rails g model Article title body user:references

* When do I use `has_many` vs `has_many :through`?

has many is when there is a simple one => many relationship between two tables, but if there is a table that is daisy-chained to another through foreign keys of an intermediary table you need to let rails know that is happening

* How can I I iterate through all of the articles associated with the current user? Write the code that would make this happen.

  <% @articles.each do |article| %>
       <%= @articles.where(user_id: article.id).title %>
  <% end %>

* How can I create a new article associated with a user who has_many articles?

 def create
    @article = Article.new(title: article_params[:title], url: article_params[:url], user: current_user)
 end

* What method does Devise give us that represents a user who is logged in?

current_user

* What command runs my migrations on Heroku?

heroku run rake db:migrate

* What command will show the logs on Heroku?

heroku logs

* Describe the purpose of Heroku

it allows you to deploy a public web app for testing and production.  you essentially get to lease a micro server for free, but you can stack more (for $$) if you start getting more hits or are comsuming tons of data.

* Describe when you would use polymorphic relationships

you go polymorphic when there can be has_many relationships on either of the tables you are trying to match.  essentially there is a third intermediary table needed that serves as a 'matcher' for these items.  a playlist table, for instance, could join users to songs where one song could be connected to two people, or one person could have multiple songs
