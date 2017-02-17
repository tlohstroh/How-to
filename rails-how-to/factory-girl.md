# Install Factory Girl & Faker
* * *

Gemfile under the :development, :test group:

```
group :development, :test do
  # ...

  gem 'factory_girl_rails', '4.7.0'
  gem 'faker', '1.6.6'
end
```

run bundle install.

Add to spec/support/factory_girl.rb file:

```
# spec/support/factory_girl.rb

RSpec.configure do |config|
  config.include FactoryGirl::Syntax::Methods
end
```

Enable the autoloading of the support directory by uncommenting the following line in your spec/rails_helper.rb:

```
Dir[Rails.root.join('spec/support/**/*.rb')].each { |f| require f }
```

Before we move forward, let's also add the following code to your spec/support/devise.rb file:

```
# spec/support/devise.rb

RSpec.configure do |config|
  config.include Devise::Test::ControllerHelpers, type: :controller
  config.include Devise::Test::ControllerHelpers, type: :view
  config.include Warden::Test::Helpers
end
```

# Example Factories

### Example Room Factory
Let's create the factory for our Room model in a new file spec/factories/rooms.rb like this:

```
FactoryGirl.define do
  factory :room do
    home_type         "House"
    room_type         "Shared"
    accommodate       2
    bedroom_count     2
    bathroom_count    3
    listing_name      { Faker::Lorem.sentence(2) }
    description       { Faker::Lorem.sentence(40) }
    address           { Faker::Address.city }
    has_tv            true
    has_kitchen       true
    has_airco         true
    has_heating       true
    has_internet      true
    price             { Faker::Commerce.price }

    trait :active do
      active true
    end

    trait :inactive do
      active false
    end
  end
end
```

To use the factory, you can use any of the following statements inside your spec:

```
# `build` creates a Room object without saving
build :room, :active

# `build_stubbed` creates a Room object and acts as an already saved Room
build_stubbed :room, :active

# `create` creates a Room object and saves it to the database
create :room, :active
create :room, :inactive

# `create_list` creates a collection of objects for a given factory
# you can also use `build_list` and `build_stubbed_list`
create_list :room, 2
```

### Example Profile Factory

Let's create the factory for our Profile model in a new file spec/factories/profiles.rb like this:

```
FactoryGirl.define do
  factory :profile do
    first_name  { Faker::Name.first_name }
    last_name   { Faker::Name.last_name }
    bio         { Faker::Lorem.sentence }
  end
end
```
### Example User Factory

Finally let's create the factory for the User model in a new file spec/factories/users.rb like this:

```
FactoryGirl.define do
  factory :user do
    email    { Faker::Internet.email }
    password { Faker::Internet.password }
  end
end
```
