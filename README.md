# Bootstrap RVM and RSpec for plain Ruby
Simple steps to bootstrap a ruby app

## Setup

### RVM
List RVM versions: ```rvm list```

Create new RVM environment with rvmrc

```rvm use <ruby_version>@gemset-name --rvmrc --create```

### Directory Layout

```
└── application_root
    ├── .rspec
    ├── Gemfile
    ├── Rakefile
    ├── lib
    │   └── app.rb
    └── spec
        └── app_spec.rb
```

### Set up the `Gemfile`
```
source "https://rubygems.org"

gem 'rspec'
```

### RSpec

* Add some color to RSpec output by adding the following to the `.rspec` file 
```
--color
```

* Set `rspec spec` as your default rake task. That way, you can simply type `rake` to run your test suite. Save this code to your Rakefile:
```
begin
  require 'rspec/core/rake_task'
  RSpec::Core::RakeTask.new(:spec)
  task default: :spec
rescue LoadError
  # rspec not available
end
```

* In the app_spec.rb file, at the top of the document, make sure to include:
```
require "rspec"
require_relative "../lib/app"
```
Where app is the name of the app.rb file. Now your spec file is linked to your app file, and ready to rock and roll. Make sure, if you haven't already got the gem in the current gemset that you run:

### Bundle
* Make sure RVM gemset is active
```
rvm gemset list
```

* Get bundler
```
gem install bundle --no-ri --no-rdoc
```

* Install RSpec
```
bundle
```
To download RSpec and get moving.

## RSpec for CoderPad
```ruby
require 'rspec/autorun'

class Class
end

RSpec.describe Class do
  it '' do
    expect().to eq
  end

end
```



