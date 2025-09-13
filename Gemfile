# Gemfile (맥/윈도우 혼용용 최적화)

source "https://rubygems.org"

# GitHub Pages 지원 버전으로 통일
gem "github-pages", group: :jekyll_plugins

# Ruby 3.x 환경에서 로컬 serve 실행 시 필요
gem "webrick", "~> 1.8"

group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.12"
  gem "jekyll-remote-theme"
end

# 윈도우 전용 젬 'platforms' 조건으로만 로드
platforms :mingw, :x64_mingw, :mswin do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
  gem "wdm", "~> 0.1"
end

# JRuby 환경용
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]
