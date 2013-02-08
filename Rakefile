require 'rubygems'
require 'rake'
require 'yaml'
require 'time'

SOURCE = "."
CONFIG = {
  'layouts' => File.join(SOURCE, "_layouts"),
  'posts' => File.join(SOURCE, "_posts"),
  'post_ext' => "md",
}

# Usage: rake post title="A Title" [date="2012-02-09"]
desc "Begin a new post in #{CONFIG['posts']}"
task :post do
  abort("rake aborted: '#{CONFIG['posts']}' directory not found.") unless FileTest.directory?(CONFIG['posts'])
  title = ENV["title"]
  abort("rake aborted: no title") if title.strip.empty?
  slug = title.downcase.strip.gsub(' ', '-').gsub(/[^\w-]/, '')
  begin
    date = (ENV['date'] ? Time.parse(ENV['date']) : Time.now).strftime('%Y-%m-%d')
  rescue Exception => e
    puts "Error - date format must be YYYY-MM-DD, please check you typed it correctly!"
    exit -1
  end
  filename = File.join(CONFIG['posts'], "#{date}-#{slug}.#{CONFIG['post_ext']}")
  if File.exist?(filename)
    abort("rake aborted: #{filename} already exists!")
  end
  
  puts "Creating new post: #{filename}"
  open(filename, 'w') do |post|
    post.puts "---"
    post.puts "layout: post"
    post.puts "title: \"#{title.gsub(/-/,' ')}\""
    post.puts 'description: ""'
    post.puts "category: "
    post.puts "tags: []"
    post.puts "---"
  end
end # task :post

# # Usage: rake page name="about.html"
# # You can also specify a sub-directory path.
# # If you don't specify a file extention we create an index.html at the path specified
# desc "Create a new page."
# task :page do
#   name = ENV["name"] || "new-page.md"
#   filename = File.join(SOURCE, "#{name}")
#   filename = File.join(filename, "index.html") if File.extname(filename) == ""
#   title = File.basename(filename, File.extname(filename)).gsub(/[\W\_]/, " ").gsub(/\b\w/){$&.upcase}
#   if File.exist?(filename)
#     abort("rake aborted!") if ask("#{filename} already exists. Do you want to overwrite?", ['y', 'n']) == 'n'
#   end
#   
#   mkdir_p File.dirname(filename)
#   puts "Creating new page: #{filename}"
#   open(filename, 'w') do |post|
#     post.puts "---"
#     post.puts "layout: page"
#     post.puts "title: \"#{title}\""
#     post.puts 'description: ""'
#     post.puts "---"
#     post.puts "{% include JB/setup %}"
#   end
# end # task :page

desc "Launch preview environment"
task :preview do
  system "jekyll --auto --server"
end # task :preview

namespace :jekyll do
  desc "start the jekyll server in auto mode"
  task :server, :num_posts do |t, args|
    num_posts = args[:num_posts]
    cmd = "jekyll --auto --server --pygments"
    cmd += " --limit_posts #{num_posts}" if num_posts
    puts "running #{cmd}"
    exec(cmd)
  end 
end