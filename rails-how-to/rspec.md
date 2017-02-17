#RSpec
##testing

https://github.com/rspec/rspec-rails
https://github.com/teamcapybara/capybara
```
#Gemfile

group :development, :test do
  gem 'rspec-rails', '~> 3.5', '>= 3.5.2'
end


group :test do
  gem 'capybara', '~> 2.9', '>= 2.9.1'
end

```

Then install the gems by going back into your terminal and typing:

```
bundle install
```

If you want to double-check that all the gem dependencies in the Gemfile are now satisfied, type:

```
bundle check
```
And you should get the following confidence-boosting output:

```
The Gemfile\'s dependencies are satisfied
```
Then, to set up RSpec for our application, run the RSpec install generator like so:

```
rails generate rspec:install
```

Finally, just as a quick sanity check, run the rspec command:

```
rspec
```
You know you have RSpec installed correctly if you see output like this:

```
No examples found.

Finished in 0.00037 seconds (files took 0.12081 seconds to load)
0 examples, 0 failures
```
