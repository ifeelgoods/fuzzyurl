require 'rake/testtask'

task :default => [:test]

Rake::TestTask.new do |t|
  t.libs << 'test'
  t.libs << 'test/lib'
  t.test_files = FileList['test/**/*_test.rb']
  #t.warning = true
  t.verbose = true
end

task :release do
  system(<<-EOT)
    git add lib/fuzzy_url/version.rb
    git commit -m 'release v#{FuzzyURL::VERSION}'
    git push origin
    git tag v#{FuzzyURL::VERSION}
    git push --tags origin
    gem build fuzzy_url.gemspec
    gem push fuzzyurl-#{FuzzyURL::VERSION}.gem
  EOT
end

