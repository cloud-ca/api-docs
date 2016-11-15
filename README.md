# cloud.ca API docs

The docs themselves are available at https://cloud-ca.github.io/api-docs

## Getting Started with Slate

### Prerequisites

You're going to need:

 - **Linux or OS X** — Windows may work, but is unsupported.
 - **Ruby, version 2.0 or newer**
 - **Bundler** — If Ruby is already installed, but the `bundle` command doesn't work, just run `gem install bundler` in a terminal.

### Getting Set Up

1. `brew install ruby` to upgrade your Ruby install
2. `gem install bundler`
3. `git clone git@github.com:cloud-ca/api-docs.git`
4. `cd api-docs`
5. Initialize and start Slate. You can either do this locally, or with Vagrant:

```shell
# either run this to run locally
bundle install
bundle exec middleman server

# OR run this to run with vagrant
vagrant up
```

You can now see the docs at http://localhost:4567. Whoa! That was fast!

Now that Slate is all set up your machine, you'll probably want to learn more about [editing Slate markdown](https://github.com/lord/slate/wiki/Markdown-Syntax), or [how to publish your docs](https://github.com/lord/slate/wiki/Deploying-Slate).

If you'd prefer to use Docker, instructions are available [in the wiki](https://github.com/lord/slate/wiki/Docker).

### Working on the docs

The main place to set up your includes is `source/index.html.md`. The includes themselves are in `source/includes` and must start with an underscore. Only one level of folder nesting is currently supported for includes (eg. `compute/instances.md`, but not `services/compute/instances.md`).

When writing new docs, put them in their own branch and merge them back into master.

### Deploying

TODO: update with instructions on deploying the docs with jenkins

1. Make sure your changes have been merged into `master`
2. `git checkout deployment`
3. `git merge master`
4. `./deploy.sh`

The docs should go live once GitHub processes the new `gh-pages` branch contents.