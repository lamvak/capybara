require 'rubygems'
require 'rspec/core/rake_task'
require 'cucumber/rake/task'
require 'yard'

desc "Run all examples"
RSpec::Core::RakeTask.new(:spec) do |t|
  t.rspec_opts = %w[--color]
end
  
RSpec::Core::RakeTask.new(:spec_with_chrome) do |t|
  t.rspec_opts = %w[--color]
  t.pattern = './spec{,/*/**}/*{_spec.rb,_spec_chrome.rb}'
end

YARD::Rake::YardocTask.new do |t|
  t.files   = ['lib/**/*.rb']
  #t.options = ['--any', '--extra', '--opts'] # optional
end

Cucumber::Rake::Task.new(:cucumber) do |task|
  task.cucumber_opts = ['--format=progress', 'features']
end

task :travis => [:spec_with_chrome, :cucumber]

task :default => [:spec, :cucumber]
