
TEST_DIR = "test"
SOURCE = "src/coffeelint.coffee"
LIB_DIR = "lib"
LINT_CONFIG = "test/fixtures/fourspaces.json"

# Print a notification.
def notify(message)
  padding = 4
  line = '*' * (message.length + padding)
  puts line
  puts "* #{message.downcase} *"
  puts line
end

desc "Run unit tests."
task :test => [:compile] do
  sh("vows --spec test/*.coffee")
  notify("tested!")
end

desc "Lint the linter."
task :lint => [:compile] do
  sh("./bin/coffeelint -f #{LINT_CONFIG} src/*.coffee test/*.coffee")
  notify("linted!")
end

desc "Compile the source."
task :compile do
  sh("coffee -c -o #{LIB_DIR} #{SOURCE}")
  notify("compiled!")
end

desc "Compile the source when it changes."
task :watch do
  sh("coffee -wc -o #{LIB_DIR} #{SOURCE}")
end

desc "Create a distribution."
task :dist => [:compile, :test, :lint]

task :default => :test