# Gemfile (정리본)

source "https://rubygems.org"

# ✅ GitHub Pages가 지원하는 Jekyll/테마/플러그인 버전을 한 번에 고정
gem "github-pages", group: :jekyll_plugins

# ✅ Ruby 3.x 로컬 개발 시 필요 (없으면 serve가 안 뜰 수 있음)
gem "webrick", "~> 1.8"

group :jekyll_plugins do
  # ✅ Pages 호환 플러그인
  gem "jekyll-feed", "~> 0.12"

  # ✅ 깃헙 원격 테마(예: minimal-mistakes) 사용 시 필요
  gem "jekyll-remote-theme"
end

# (Windows/JRuby 환경용 보조 젬은 필요 시 유지)
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

gem "wdm", "~> 0.1", :platforms => [:mingw, :x64_mingw, :mswin]
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]
