# TODO

Goal: make a gem that will change a Gemfile to install gems from their source repository (GitHub, GitLab, Bitbucket, etc) using Bundler's for git locations.

```ruby
# examples
gem 'nokogiri', '1.7.0.1', git: 'https://github.com/sparklemotion/nokogiri'
gem 'cf-copilot', git: 'https://github.com/cloudfoundry/copilot', glob: 'sdk/ruby/*.gemspec'
git 'https://github.com/rails/rails.git' do
  gem 'railties'
  gem 'actionpack'
  gem 'activemodel'
end
git 'https://github.com/rails/rails.git', ref: '4aded' do
git 'https://github.com/rails/rails.git', branch: '5-0-stable' do
git 'https://github.com/rails/rails.git', tag: 'v5.0.0' do
gem 'rails', github: 'rails', ref: 'a9752dcfd15bcddfe7b6f7126f3a6e0ba5927c56'
gem 'keystone', bitbucket: 'musicone/keystone'
gem 'my_gist', gist: '4815162342'
```

Reference: https://bundler.io/guides/git.html

## Development guielines

- Always latest ruby
- Always latest bundler
- Always latest rubygems
- Use Seattle.rb style
- Test first!
- Use RSpec
- Small and simple is better than big and complex (methods, files, PRs, etc)
-

## Unorganized tasks

- [_] Use Bundler to analyze and understand Gemfile
- [_] Check for already installed gems in Gemfile
    - [_] Use their .gemspec for remote repo info
- [_] Fetch remote gemspecs
  - [_] Or scrape gem host for gem remote repo info
- [_] For each gem repo, figure out how to does versioning
  - [_] Tags, branches, GitHub Releases, some other secret third thing
- [_] How to handle private repositories?
- [_] Add git keyword args to `gem` lines in Gemfile
- [_] Try to maintain existing formatting
- [_] Check checksums for increased security and safety
- [_] Create CLI
    - [_] decentralize path_to_gemfile (default: './Gemfile')
    - [_] -h --help
    - [_] -v --version
    - [_] -dry-run
    - [_] -i --interactive : asks for confirmation/choice of git remote args
