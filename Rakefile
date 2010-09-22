require 'rubygems'
require 'rake'
require 'rake/testtask'
require 'rake/rdoctask'

desc 'Default: run unit tests.'
task :default => :test

desc 'Test the migration_fu plugin.'
Rake::TestTask.new(:test) do |t|
  t.libs << 'lib'
  t.pattern = 'test/**/*_test.rb'
  t.verbose = true
end

desc 'Generate documentation for the migration_fu plugin.'
Rake::RDocTask.new(:rdoc) do |rdoc|
  rdoc.rdoc_dir = 'rdoc'
  rdoc.title    = 'MigrationFu'
  rdoc.options << '--line-numbers' << '--inline-source'
  rdoc.rdoc_files.include('README')
  rdoc.rdoc_files.include('lib/**/*.rb')
end

namespace :test do
  desc 'Measure test coverage'
  task :coverage do
    system("rcov --rails --text-summary -Ilib --xrefs --html test/unit/*_test.rb") 
    #test/functional/*_test.rb test/views/*_test.rb test/integration/*_test.rb")
    system("open coverage/index.html") if PLATFORM['darwin']
    system("firefox coverage/index.html") if PLATFORM['linux']
  end
end

Dir["#{File.dirname(__FILE__)}/tasks/*.rake"].sort.each { |ext| load ext }

require 'jeweler'
jt = Jeweler::Tasks.new do |gem|
  gem.name = "artemk-migration_fu"
  gem.summary = "Add and remove FK in MYSQL"
  gem.description = "Add and remove FK in MYSQL"
  gem.email = "artemk@svitla.com"
  gem.has_rdoc = false
  gem.files    = FileList[
    "README",
    "lib/**/*.rb",
    "init.rb"
  ]
  gem.test_files = FileList[
    "test/**/*.rb"
  ]
end
Jeweler::GemcutterTasks.new

