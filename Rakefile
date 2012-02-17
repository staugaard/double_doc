require "bundler/gem_tasks"

$LOAD_PATH.unshift 'lib'

require 'double_doc/task'

desc "Generate documentation"
DoubleDoc::Task.new(:doc,
  :sources => 'doc/readme.md',
  :md_destination => '.',
  :html_destination => 'site',
  :title => 'API Documentaion'
)

desc "Publish docs to github"
task :publish => :doc do
  `git add doc`
  `git add readme.md`
  `git commit -m 'Updated documentation'`
  `git push origin master`
  `git checkout gh-pages`
  `cp site/screen.css .`
  `cp site/readme.html index.html`
  `git commit -a -m 'Updated site'`
  `git push origin gh-pages`
  `git co master`
end

task :default => [:doc]
