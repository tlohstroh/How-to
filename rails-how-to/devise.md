https://github.com/plataformatec/devise

# Install Devise
***
Devise is the standard, secure way to set up authentication for any Rails app. You should use Devise whenever you need your Users to sign up for your website and have an account.

First add the gem to your Gemfile:

```
# Gemfile

gem 'devise'
```

Then install the bundle and initialize Devise:

```
bundle install
rails generate devise:install
```

Create the devise driven User model:

```
rails generate devise User
rails db:migrate
```
Some setup you must do manually if you haven't yet:


  1. Ensure you have defined default url options in your environments files. Here
     is an example of default_url_options appropriate for a development environment
     in config/environments/development.rb:

       config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }

     In production, :host should be set to the actual host of your application.

  2. Ensure you have defined root_url to *something* in your config/routes.rb.
     For example:

       root to: "home#index"

  3. Ensure you have flash messages in app/views/layouts/application.html.erb.
     For example:

       <p class="notice"><%= notice %></p>
       <p class="alert"><%= alert %></p>

  4. You can copy Devise views (for customization) to your app by running:

       rails g devise:views
```
```
We will be updating the Devise views (the sign in/up screen, etc), so let's generate the views with the following generator command:

```
rails generate devise:views
```


Add this line at the end of config/environments/development.rb:

```
config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }
```
Add flash messages in app/views/layouts/application.html.erb:

```
<p class="notice"><%= notice %></p>
<p class="alert"><%= alert %></p>
```

Start up your server, and visit the page http://localhost:3000/users/sign_up.
