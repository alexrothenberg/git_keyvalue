# git_keyvalue

This gem provides a GET/PUT-style wrapper for a remote git repo.

In effect, it presents the repo as a key/value store, where every key
is a path (always interpreted relative to the repo's root) and every
key's value is just the contents of the file at that path.

You can directly get/put the string contents of files. Or you can use
getfile/putfile to copy files from/into the repo, which will be more
efficient for large binary files like videos or images.

## Installation

Add this line to your application's Gemfile:

    gem 'git_keyvalue'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install git_keyvalue

## Usage

An example:

    $  require 'rubygems'
    $  require 'bundler/setup
    $  require 'git_keyvalue'
    $  # make sure you have network and permissions access to the repo URL
    $  # which can be any valid git URL (i.e.: http, ssh, git, or file schemes)
    $  g = GitKeyvalue::KeyValueRepo.new('http://githuben.com/path/to/repo/')
    $  g.get('metadata/file1.txt')
    $  => 'I am the contents of metadata/file1.txt!'
    $  g.put('metadata/file1.txt','new contents of metadata/file1.txt')
    $  => nil
    $  # remote repo has now been updated
    $  g.put('metadata/file2.txt','contents for metadata/file2.txt')
    $  => nil
    $  # you just created a new file file2.txt, in metadata/, in the remote repo

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## Compiling the docs

Do ``gem install yard`` to ensure you have yard installed.

Compile the docs from source docstrings with ``rake yard``.

Do ``yard server --reload`` to start a webserver where you can browse
the generated HTML.


