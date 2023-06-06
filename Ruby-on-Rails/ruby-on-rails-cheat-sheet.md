# Ruby on Rails cheat sheet

The cheat sheet covers some common commands, syntax, and concepts for Rails development

- [Ruby on Rails cheat sheet](#ruby-on-rails-cheat-sheet)
  - [Rails CLI](#rails-cli)
  - [Rails generators CLI](#rails-generators-cli)
  - [Migration](#migration)
  - [Routes](#routes)
  - [Model](#model)
  - [Active Record](#active-record)
  - [Template](#template)
  - [Form](#form)
  - [Flash, Session and Cookie](#flash-session-and-cookie)

## Rails CLI

| Command                  | Explanation            |
| ------------------------ | ---------------------- |
| `rails new project_name` | Create a new rails app |
| `rails s`                | Start the Rails server |
| `rails c`                | Rails console          |
| `bundle install`         | Install dependencies   |
| `rails routes`           | View all routes        |
| `rails dev:cache`        | Toggle rails caching   |

## Rails generators CLI

| Command                                              | Explanation                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| `rails g scaffold Product name:string price:decimal` | CRUD Scaffold (model, migrations, controller, views, test) |
| `rails g scaffold Invoice customer:references`       | CRUD Scaffold with one to many relationship field          |
| `rails destroy scaffold Product`                     | Delete scaffold created files                              |
| `rails g controller Products index show`             | Controller (name, action1, action2, ...)                   |
| `rails g model Product name:string active:boolean`   | Model, migration and table columns                         |
| `rails destroy scaffold Story`                       | Reverse a generated scaffold                               |
| `rails destroy controller Story`                     | Reverse a generated controller                             |
| `rails destroy model Story`                          | Reverse a generated model                                  |

## Migration

| Command                                                | Explanation                                |
| ------------------------------------------------------ | ------------------------------------------ |
| `rails g migration Table`                              | Create new table migration                 |
| `rails g migration add_comment_to_tables comment:text` | Update existing table migration            |
| `rails db:migrate`                                     | Run migration                              |
| `rails db:create`                                      | create db                                  |
| `rails db:drop`                                        | Delete db                                  |
| `rails db:seed`                                        | Run database seed code                     |
| `rails db:rollback`                                    | Rollback last migration                    |
| `rails db:reset`                                       | Delete and re-create db and run migrations |

## Routes

```ruby
# Route maps to controller#action
get 'welcome', to: 'pages#home'

# Root page (root_path name helper)
root 'pages#home' 

# Named route 
get 'exit', to: 'sessions#destroy', as: :logout

# Create all the routes for a RESTful resource
resources :items

# HTTP    Verb Path    Controller#Action  Named Helper
# GET     /items           items#index    items_path
# GET     /items/new       items#new      new_item_path
# POST    /items           items#create   items_path
# GET     /items/:id       items#show     item_path(:id)
# GET     /items/:id/edit  items#edit     edit_item_path(:id)
# PUT     /items/:id       items#update   item_path(:id)
# DELETE  /items/:id       items#destroy  item_path(:id)

# Only for certain actions
resources :items, only: :index

# Resource with exceptions 
resources :items, except: [:new, :create]

# Nested resources
resources :items do
  resources :reviews
end
# create 7 RESTful for items and reviews 
# :reviews will have /items/item:id prefixing each routes
# GET /items/:item_id/reviews  reviews#index  item_reviews_path 

# Dynamic segment: params['id']
get 'products/:id', to: 'products#show'
# Query String: url /products/1?user_id=2
# params will be {'id' 'user_id'}

# Namespace Admin::ArticleController
# and prefix '/admin'
namespace :admin do
  resources :articles
end

# only prefix '/admin'
scope '/admin' do
  resources :articles, :comments
end

# Redirect
get '/stories', to: redirect('/articles')
```

## Model

```ruby
# Model validation
validates :title, :description, :image_url, presence: true
validates :email, presence: true, format: { with: /\A[^@\s]+@[^@\s]+\z/, message: 'Must be a valid email address'}
validates :price, numericality: { greater_than_equal_to: 0.01 }
validates :title, uniqueness:  true
validates :title, length: { minimum: 3, maximum: 100 }
validates :type, inclusion: types.keys

# Model relationship
belongs_to :customer

# Relation with cascade delete
has_many :invoices, dependent: :destroy

#One to one
has_one :profile

# Hook methods 
before_destroy :ensure_not_reference_by_any_invoices 
before_save :downcase_email 

# create virtual password and password_confirmation 
# and bcrypt password_digest
# add method to model: user.authenticate(params[:password])
has_secure_password
```

## Active Record

```ruby
# Active record common methods
Article.all
# Throw error if not found
Article.find(params[:id])
# Do not throw error if not found
Article.find_by(product_id: product_id)
@category = Category.find_by!(slug: params['slug']) # Return Not Found Error (404 page in production)
Article.group(:product_id).sum(:quantity)
Article.where('quantity > 1')
Article.where(cat_id: cat_id, model: model)
Article.where(model: model).or(Article.where(cat_id: cat_id))
Article.join(:categories).where(categories: { id: 2 } )
Article.where("title LIKE ?", "%" + params[:q] + "%")
Article.count
Article.first
Article.last
Article.column_names # ['id', 'name', 'price']
Category.delete_all # delete all rows in Category table
product.category = Category.all.sample # random for Faker data
@products = Product.offset(5).limit(10).all # skip 5, take 10
```

## Template

```ruby
<%# Comment tag %>

<%# Output return expression tag %>
<%= @user.name %>

<%# No output return expression tag %>
<% if @user.name == 'Mike' %>

<%# Layout file : app/view/layouts/application.html.erb %>

<%# In layout file replace expression with page content %>
<%= yield %>

<%# View for the route name helper path %>
<%= link_to 'About', about_path, class: 'nav-link' %>

<%# View for the route name helper path with params %>
<%= link_to 'Item record', item_path(@item) %>

<%# auto object to route map (/products/:id) %>
<%= link_to 'Show', @product %>

<%# Delete link %>
<%= link_to 'Destroy', product, method: :delete, data: { confirm: 'Are you sure?' } %>

<%# Post link %>
<%= button_to 'Add to Cart', line_items_path(product_id: product) %>

# link_to with slot
<%= link_to category_path do %>
  <%= @product.category.name %>
<% end %>

<%# Button form %>
<%= button_to 'Logout', logout_path, method: :delete %>

<%# Image asset (app/assets/images) %>
<%= image_tag "rails.png" %>

<%# Format currency %>
<%= number_to_currency(product.price) %>

<%# Safe Html render %>
<%= sanitize(product.description) %>

<%# Enable caching %>
<%= cache @products do %>

<%# Check url %>
<%= request.path.include?('post') ? 'active' : '' %>">

<%# Check current page %>
<%= current_page?('about') ? 'active' : '' %>">

<%# Render shared partial _navbar.html.erb %>
<%= render partial: 'shared/navbar' %>

<%# Render partial _form.html.erb %>
<%= render 'form', product: @product %>

<%# data tables iterations %>
<% @users.each do |user| %> <% end %>

<%# Render a for each _user.html.erb %>
<%= render @users %> 

<%# Conditional %>
<% if current_user.signed_in? %> 
  ...
<% else %> 
  ...
<% end %>

<%# Display errors %>
<% if @post.errors.any? %> 
<% if form.object.errors.any? %>

<% if @post.errors.empty? %>
<% @post.errors.full_messages.each do |message| %>
  <p class='error'><%= message %></p>
<%= user.errors.count %>
<%= post.errors[:description] %>

<%# Flash messages %>
<% flash.each do |msg_type, msg| %>
  <div class="alert alert-<%= msg_type %>">
    <%= msg %>
  </div>
<% end %>
```

## Form

```ruby
<%# Model form %>
<%= form_with(model: product), local: true do |form| %>
  <%= form.label :title %>
  <%= form.text_field :title, class: 'form-control' %>

  <%= form.submit %>
<% end %>

<%# Generic form %>
<%= form_with url: "/search", method: :get, local: true do |form| %>
  <%= form.label :query, "Search for:" %>
  <%= form.text_field :query, placeholder: 'search' %>
  <%= form.submit "Search", class: 'btn btn-primary' %>
<% end %>

<%# Multi-lines memo %>
<%= form.text_area :description, rows: 10, cols: 60 %>

<%# Collection Select (field, collection, key, value, label) %>
<%= form.collection_select :category_id, Category.all, :id, :name, {include_blank: '- Select a Category -'}, {class: 'form-select'}

<%# Select %>
<%= form.select :type, Customer.types.keys, prompt: 'Select a type' %>
<%= form.select :rating, (1..5) %>

<%# if form in new or edit mode change submit text %> 
<%= form.submit @product.new_record? ? 'Create' : 'Update', class: "mt-4 btn btn-primary" %>
```

## Flash, Session and Cookie

```ruby
# Create flash (reset every new request)
flash[:success] = 'User created with success!'

# Create flash.now (reset every new view render)
flash.now[:error] = 'Please select s user!'

# Create session (reset every browser close)
session[:user_id] = user.id

# Check if session exist
session[:user_id].nil?

# Remove
session.delete(:user_id)

# Remove all
reset_session      

# Create cookie (reset at expiration date)
cookies.permanent[:remember_token] = remember_token

# Encrypted cookie
cookies.permanent.encrypted[:user_id] = user.id

# Delete cookie
cookies.delete(:user_id)
```
