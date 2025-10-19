# Decentralize

⚠️ **Under construction** ⚠️
A tool to modify a `Gemfile` so that each gem can be installed from its source.

Goal: install gems from the source code repo, not a gem server

## Tradeoffs

- ❌ **Ergonomics:** A `Gemfile` full of `git`, `tag`, `branch` args is uglier
- ❌ **Performance:** Installing gems from source repos is probably slower than installing from a gem server
- ❌ **Transitive dependencies:** Gems in `Gemfile` get installed from source repo (`git`, `github`, etc), but transitive dependencies are not installed from source repos. Is there a way to install transitive dependencies from source repos?
- ❌ **Bootstrapping:** This gem needs to phone home to a gem server to fetch metadata for `Gemfile` gems

- ⚠️ **Updates:** Will Dependabot version bump PRs Just Work?
- ⚠️ **Namespaces:** Will this leads to multiple gems of the same name/space colliding?
- ⚠️ **Phishing:** Will this enable phishing attacks?
- ⚠️ **Discovery:** Will discovery of gems be harder if we’re installing from source repos?
- ⚠️ **Security:** Will this introduce security vulnerabilities? Checksums!?

- ✅ **Decentralization:** Installing gems doesn’t depend on any gem server, sort of (but it does depend on a gem server for metadata)
- ✅ **Transparency:** Installing gems from source repos is more transparent than installing from a gem server
- ✅ **Resilience:** Makes it harder for a bad actor to takeover a gem

## Examples

`Gemfile`and `Gemfile.lock` examples are in `/spec/examples`.

## Installation

Install the gem and add to the application’s `Gemfile` by executing:

```sh
bundle add decentralize
```

If Bundler is not being used to manage dependencies, install the gem by executing:

```sh
gem install decentralize
```

## Usage

Hypothetical CLI usage:

```sh
decentralize # easiest usage
decentralize path/to/Gemfile # default: ./Gemfile
```

Optional args:

```sh
# print help
decentralize -h
decentralize --help

# print version
decentralize -v
decentralize --version

# dry run, print what would happen without modifying files
decentralize -dry-run

# asks for confirmation/choice of git remote args
decentralize -i --interactive
```

## Development

After checking out the repo, run `bin/setup` to install dependencies.
Then, run `rake spec` to run the tests.
You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`.
To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`,
which will create a git tag for the version, push git commits and the created tag, and push the `.gem` file to
[rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/veganstraightedge/decentralize.
This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the
[code of conduct](https://github.com/veganstraightedge/decentralize/blob/main/CODE_OF_CONDUCT.md).

## License

The gem is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).

## Code of Conduct

Everyone interacting in the Decentralize project’s codebases,
issue trackers, chat rooms and mailing lists is expected to follow the
[code of conduct](https://github.com/veganstraightedge/decentralize/blob/main/CODE_OF_CONDUCT.md).
