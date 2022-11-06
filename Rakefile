# frozen_string_literal: true

require "rake/testtask"

task default: :test

task :package

Rake::TestTask.new do |t|
  t.pattern = "test/**/*_test.rb"
  t.warning = true
  t.verbose = true
  t.ruby_opts = ["--dev"] if defined?(JRUBY_VERSION)
end

namespace :test do
  task :isolated do
    Dir.glob("test/**/*_test.rb").all? do |file|
      sh(Gem.ruby, "-w", file)
    end || raise("Failures")
  end
end
