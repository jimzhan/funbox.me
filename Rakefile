require 'rubygems'
require 'rake'
require 'rdoc'
require 'date'
require 'yaml'
require 'tmpdir'
require 'jekyll'
require 'shellwords'


desc "Cleaning existing resources..."
task :clean do
    system "jekyll clean -s . -d _site"
end

desc "Start building static resources..."
task :build => [:clean] do
  config = Jekyll.configuration({
    "source"      => ".",
    "destination" => "_site"
  })
  Jekyll::Site.new(config).process
end

desc "Starting Jekyll instance..."
task :default => [:build] do
    system "bundle exec jekyll serve"
end

desc "Start pushing resources onto gh-pages..."
task :push => [:build] do
  Dir.mktmpdir do |tmp|
    message = Shellwords.escape("Autocommit by Rakefile at #{Time.now.utc}")
    system "git add ."
    system "git commit -am #{message}"
    system "git push origin gh-pages --verbose"
  end
end
