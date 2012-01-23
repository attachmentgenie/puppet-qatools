# encoding: utf-8

require 'rubygems'
require 'bundler'
begin
  Bundler.setup(:default, :development)
rescue Bundler::BundlerError => e
  $stderr.puts e.message
  $stderr.puts "Run `bundle install` to install missing gems"
  exit e.status_code
end
require 'rake'

require 'jeweler'
Jeweler::Tasks.new do |gem|
  # gem is a Gem::Specification... see http://docs.rubygems.org/read/chapter/20 for more options
  gem.name = "puppet-qatools"
  gem.homepage = "http://github.com/attachmentgenie/puppet-qatools"
  gem.license = "MIT"
  gem.summary = %Q{Meta Package for the Puppet Quality Assurance Toolchain}
  gem.description = %Q{Meta Package for the Puppet Quality Assurance Toolchain}
  gem.email = "bram@attachmentgenie.com"
  gem.authors = ["attachmentgenie"]
  # dependencies defined in Gemfile
  gem.add_dependency 'cucumber-puppet'
  gem.add_dependency 'finger-puppet'
  gem.add_dependency 'puppet-lint'
  gem.add_dependency 'puppet-module'
  gem.add_dependency 'puppet-profiler'
  gem.add_dependency 'rspec-puppet'
end
Jeweler::RubygemsDotOrgTasks.new

require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.libs << 'lib' << 'test'
  test.pattern = 'test/**/test_*.rb'
  test.verbose = true
end

require 'rcov/rcovtask'
Rcov::RcovTask.new do |test|
  test.libs << 'test'
  test.pattern = 'test/**/test_*.rb'
  test.verbose = true
  test.rcov_opts << '--exclude "gems/*"'
end

task :default => :test

require 'rdoc/task'
Rake::RDocTask.new do |rdoc|
  version = File.exist?('VERSION') ? File.read('VERSION') : ""

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "puppet-qatools #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end
