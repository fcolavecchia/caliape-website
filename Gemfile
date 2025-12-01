source "https://rubygems.org"

# Gema de Jekyll
gem "jekyll", "~> 4.3.3"

# Gemas requeridas para Ruby 3.4+
gem "csv"
gem "logger"
gem "base64"

# Plugins de Jekyll
group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.12"
  gem "jekyll-seo-tag", "~> 2.8"
end

# Compatibilidad con Windows y JRuby
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

# Mejora de rendimiento para watchear directorios en Windows
gem "wdm", "~> 0.1", :platforms => [:mingw, :x64_mingw, :mswin]

# Lock `http_parser.rb` gem to `v0.6.x` en JRuby
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]
