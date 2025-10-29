# frozen_string_literal: true

source "https://rubygems.org"

# Core dependencies
gem "jekyll", "~> 4.3"
gem "jekyll-theme-chirpy", "~> 7.2", ">= 7.2.4"

# Build dependencies
gem "webrick" # Required for local serve on Ruby >= 3.0
gem "html-proofer", "~> 5.0", group: :test

# Platform compatibility
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

# Optional for Windows file watching
gem "wdm", "~> 0.2.0", platforms: [:mingw, :x64_mingw, :mswin]
