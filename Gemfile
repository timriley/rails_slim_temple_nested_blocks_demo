source "https://rubygems.org"
git_source(:github) { |repo| "https://github.com/#{repo}.git" }

ruby "3.2.0"


# -----------------------------------------------------------------------------
# Slim/Temple gem pairs demonstrating that github.com/judofyr/temple/pull/112
# does not introduce a bug with Slim/Rails.
#
# Try each of these in sequence to see the bug come and go.
# -----------------------------------------------------------------------------

# 🚫 Using releases or git refs as of 21 December 2022 replicates the bug:
#
# ❯ curl -s http://localhost:3000/posts| grep microcopy
#    <divtestyes<divtestyes <divtestyes class="<divtestyes<divtestyes <divtestyes class="">awesome microcopy</div>
#
# gem "slim", github: "slim-template/slim", ref: "45a8087"
# gem "temple", "= 0.9.1"

# ✅ Using the latest releases shows the bug is no longer present:
#
# ❯ curl -s http://localhost:3000/posts| grep microcopy
#     <div class="test yes">awesome microcopy</div>
#
# gem "slim", "= 5.1.0"
# gem "temple", "= 0.10.0"

# ✅ Using latest slim plus a branch of temple with https://github.com/judofyr/temple/pull/112
# reintroduced does _not_ reintroduce the bug:
#
# ❯ curl -s http://localhost:3000/posts| grep microcopy
#     <div class="test yes">awesome microcopy</div>
#
# gem "slim", "= 5.1.0"
# gem "temple", github: "timriley/temple", branch: "propagate-options-to-capture-generator"








# -----------------------------------------------------------------------------
# Standard Rails `Gemfile` below
# -----------------------------------------------------------------------------

# Bundle edge Rails instead: gem "rails", github: "rails/rails", branch: "main"
gem "rails", "= 7.0.4"

# The original asset pipeline for Rails [https://github.com/rails/sprockets-rails]
gem "sprockets-rails"

# Use sqlite3 as the database for Active Record
gem "sqlite3", "~> 1.4"

# Use the Puma web server [https://github.com/puma/puma]
gem "puma", "~> 5.0"

# Use JavaScript with ESM import maps [https://github.com/rails/importmap-rails]
gem "importmap-rails"

# Hotwire's SPA-like page accelerator [https://turbo.hotwired.dev]
gem "turbo-rails"

# Hotwire's modest JavaScript framework [https://stimulus.hotwired.dev]
gem "stimulus-rails"

# Build JSON APIs with ease [https://github.com/rails/jbuilder]
gem "jbuilder"

# Use Redis adapter to run Action Cable in production
# gem "redis", "~> 4.0"

# Use Kredis to get higher-level data types in Redis [https://github.com/rails/kredis]
# gem "kredis"

# Use Active Model has_secure_password [https://guides.rubyonrails.org/active_model_basics.html#securepassword]
# gem "bcrypt", "~> 3.1.7"

# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem "tzinfo-data", platforms: %i[ mingw mswin x64_mingw jruby ]

# Reduces boot times through caching; required in config/boot.rb
gem "bootsnap", require: false

# Use Sass to process CSS
# gem "sassc-rails"

# Use Active Storage variants [https://guides.rubyonrails.org/active_storage_overview.html#transforming-images]
# gem "image_processing", "~> 1.2"

group :development, :test do
  # See https://guides.rubyonrails.org/debugging_rails_applications.html#debugging-with-the-debug-gem
  gem "debug", platforms: %i[ mri mingw x64_mingw ]
end

group :development do
  # Use console on exceptions pages [https://github.com/rails/web-console]
  gem "web-console"

  # Add speed badges [https://github.com/MiniProfiler/rack-mini-profiler]
  # gem "rack-mini-profiler"

  # Speed up commands on slow machines / big apps [https://github.com/rails/spring]
  # gem "spring"
end

group :test do
  # Use system testing [https://guides.rubyonrails.org/testing.html#system-testing]
  gem "capybara"
  gem "selenium-webdriver"
  gem "webdrivers"
end
