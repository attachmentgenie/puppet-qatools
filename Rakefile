# encoding: utf-8

require 'rubygems'
require 'bundler'

begin
  Bundler.setup(:default, :xzibit, :development)
rescue Bundler::BundlerError => e
  $stderr.puts e.message
  $stderr.puts "Run `bundle install` to install missing gems"
  exit e.status_code
end

require 'rake'
require 'jeweler'

Jeweler::Tasks.new do |gem|
  gem.name = "puppet-qatools"
  gem.homepage = "http://github.com/attachmentgenie/puppet-qatools"
  gem.summary = %Q{Meta Package for the Puppet Quality Assurance Toolchain}
  gem.description = %Q{Meta Package for the Puppet Quality Assurance Toolchain}
  gem.license = "MIT"
  gem.authors = ["bram vogelaar"]
  gem.email = "bram@attachmentgenie.com"
  # dependencies defined in Gemfile
end

Jeweler::RubygemsDotOrgTasks.new

require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.test_files = FileList.new('test/**/test_*.rb') do |list|
    list.exclude 'test/test_helper.rb'
    list.exclude 'test/fixtures/**/*.rb'
  end
  test.libs << 'test'
  test.verbose = true
end

namespace :test do
  task :gemspec_dup do
    gemspec = Rake.application.jeweler.gemspec
    dupped_gemspec = gemspec.dup
    cloned_gemspec = gemspec.clone
    puts gemspec.to_ruby
    puts dupped_gemspec.to_ruby
  end
end

require 'yard'
YARD::Rake::YardocTask.new do |t|
  t.files   = FileList['lib/**/*.rb'].exclude('lib/jeweler/templates/**/*.rb')
end

require 'rcov/rcovtask'
Rcov::RcovTask.new(:rcov => :check_dependencies) do |rcov|
  rcov.libs << 'test'
  rcov.pattern = 'test/**/test_*.rb'
end

require 'cucumber/rake/task'
Cucumber::Rake::Task.new(:features) do |features|
  features.cucumber_opts = "features --format progress"
end
namespace :features do
  Cucumber::Rake::Task.new(:pretty) do |features|
    features.cucumber_opts = "features --format progress"
  end
end

if ENV["RUN_CODE_RUN"] == "true"
  task :default => [:test, :features]
else
  task :default => :test
end
