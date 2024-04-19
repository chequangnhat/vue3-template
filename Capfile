
require "capistrano/setup"
require "capistrano/deploy"

# Define your servers
server "example.com", user: "deploy", roles: %w{app}

# Set your application name and repository URL
set :application, "my-vue3-app"
set :repo_url, "git@github.com:username/my-vue3-app.git"

# Define Capistrano tasks
namespace :deploy do
  desc "Build Vue.js app"
  task :build do
    on roles(:app) do
      within release_path do
        execute :npm, "install"
        execute :npm, "run", "build"
      end
    end
  end

  desc "Restart application"
  task :restart do
    # Your restart tasks (e.g., restarting web server)
  end
end

# Run build task before deploying
before "deploy:publishing", "deploy:build"
after "deploy:publishing", "deploy:restart"