# Ruby buildpack for use in Stackato

A simple ruby buildpack to deploy Rails app in Stackato. Simply runs
`bundle install` to install dependencies instead of wget'ing each gem
in Gemfile.lock which is what the CloudFoundry plugin does, among
other complicated things.

## Example stackato.yml

```
name: myapp

env:
 BUILDPACK_URL: git://github.com/ActiveState/stackato-buildpack-ruby.git

processes:
 web: bundle exec rails server

services:
 mysql: myapp-db
 # for staging cache
 myapp-cache: filesystem

mem: 512
```