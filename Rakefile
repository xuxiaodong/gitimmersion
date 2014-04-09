# Rakefile based off the one in Octopress

require "highline/import"
require "stringex"

## -- Misc Configs -- ##
source_dir      = "."      # source file directory
posts_dir       = "_posts" # directory for blog files
new_post_ext    = "md"     # default new post file extension when using the new_post task
new_page_ext    = "md"     # default new page file extension when using the new_page task
server_port     = "4000"   # port for preview server eg. localhost:4000

#######################
# Working with Jekyll #
#######################

# usage rake new[my-new-post] or rake new['my new post'] or rake new (defaults to "new-post")
desc "Begin a new post in #{source_dir}/#{posts_dir}"
task :new, :title do |t, args|
  raise "### You haven't set anything up yet. First run `rake install` to set up an Octopress theme." unless File.directory?(source_dir)
  mkdir_p "#{source_dir}/#{posts_dir}"
  args.with_defaults(:title => 'new-post')
  title = args.title
  filename = "#{source_dir}/#{posts_dir}/#{Time.now.strftime('%Y-%m-%d')}-#{title.to_url}.#{new_post_ext}"
  if File.exist?(filename)
    abort("rake aborted!") if ask("#{filename} already exists. Do you want to overwrite?", ['y', 'n']) == 'n'
  end
  puts "Creating new post: #{filename}"
  open(filename, 'w') do |post|
    post.puts "---"
    post.puts "layout: post"
    post.puts "title: #{title.gsub(/&/,'&amp;')}"
    post.puts "date: #{Time.now.strftime('%Y-%m-%d %H:%M')}"
    post.puts "post-link:"
    post.puts "---"
    post.puts ""
    post.puts ""
  end
  #system "vim #{filename}"
end

# requires ruby 1.9 :(
desc "preview the site in a web browser"
task :preview do
  raise "### You haven't set anything up yet. First run `rake install` to set up an Octopress theme." unless File.directory?(source_dir)
  puts "Starting to watch source with Jekyll. Starting Rack on port #{server_port}"
  jekyllPid = Process.spawn("jekyll --server --auto")

  trap("INT") {
    [jekyllPid].each { |pid| Process.kill(9, pid) rescue Errno::ESRCH }
    exit 0
  }

  [jekyllPid].each { |pid| Process.wait(pid) }
end
