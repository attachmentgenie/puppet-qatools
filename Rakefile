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
  gem.authors = ["bram vogelaar"]
  # dependencies defined in Gemfile
end
Jeweler::RubygemsDotOrgTasks.new
