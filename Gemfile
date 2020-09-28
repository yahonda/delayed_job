source 'https://rubygems.org'

gem 'rake'

platforms :ruby do
  # Rails 5.1 is the first to work with sqlite 1.4
  # Rails 6 now requires sqlite 1.4
  if ENV['RAILS_VERSION'] && ENV['RAILS_VERSION'].split.last < '5.1'
    gem 'sqlite3', '< 1.4'
  else
    gem 'sqlite3'
  end
end

platforms :jruby do
  if ENV['RAILS_VERSION'] == '~> 4.2.0'
    gem 'activerecord-jdbcsqlite3-adapter', '< 50.0'
  else
    gem 'activerecord-jdbcsqlite3-adapter'
  end
  gem 'jruby-openssl'
  gem 'mime-types'
  if ENV['RAILS_VERSION'] == 'edge'
    gem 'railties', :github => 'rails/rails'
  else
    gem 'railties', (ENV['RAILS_VERSION'] || ['>= 3.0', '< 5.3'])
  end
end

platforms :rbx do
  gem 'psych'
end

group :test do
  if ENV['RAILS_VERSION'] == 'edge'
    gem 'actionmailer', :github => 'rails/rails'
    gem 'activerecord', :github => 'rails/rails'
  else
    gem 'actionmailer', (ENV['RAILS_VERSION'] || ['>= 3.0', '< 5.3'])
    gem 'activerecord', (ENV['RAILS_VERSION'] || ['>= 3.0', '< 5.3'])
  end

  gem 'coveralls', :require => false
  gem 'rspec', '>= 3'
  gem 'rubocop', '>= 0.25', '< 0.49'
  gem 'simplecov', '>= 0.9'
end

gemspec
