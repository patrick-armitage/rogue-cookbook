# rogue-cookbook

A simple cookbook for experimenting with chef-server using a preconfigured
Vagrantfile, tested using ubuntu 12.04 and modified settings.

<!-- ## Supported Platforms

TODO: List your supported platforms.

## Attributes

<table>
  <tr>
    <th>Key</th>
    <th>Type</th>
    <th>Description</th>
    <th>Default</th>
  </tr>
  <tr>
    <td><tt>['rogue']['bacon']</tt></td>
    <td>Boolean</td>
    <td>whether to include bacon</td>
    <td><tt>true</tt></td>
  </tr>
</table> -->

## Usage

**NOTE:**
Vagrantfile is preconfigured to create a box with 2048MB memory.
If that's too much RAM for your system, you can try dialing it down, but
you may run into "not enough memory" issues, so it's not recommended.

* Installation (OSX instructions):
```
brew cask update
brew cask install virtualbox
brew cask install vagrant
brew cask install chefdk

vagrant plugin install vagrant-berkshelf
```

**OPTIONAL:**
Add chefdk to your PATH in .bashrc/.zshrc (it needs to be at
the beginning of your PATH):
```
export PATH="/opt/chefdk/embedded/bin:$PATH"
```

Occasionally there seems to be an issue using the proper `berkshelf` gem.
In which case, try adding to your .bashrc/.zshrc:
```
export GEM_PATH="/opt/chefdk/embedded/lib/ruby/gems/<your ruby version here>"
```
Then, install the berkshelf gem to chef's env by running:
```
/opt/chefdk/embedded/bin/gem install berkshelf --no-ri --no-rdoc
```
To insure everything is working properly, run these commands:
```
which berks
# should output /opt/chefdk/embedded/bin/berks

ls /opt/chefdk/embedded/lib/ruby/gems/<your ruby version here>/gems
# should list berkshelf among the gems
```

**ALTERNATIVE:**
It may be simpler for some to simply prepend any `berks` or `chef` commands with
`chef exec`, for example:
```
chef exec berks install
#OR
chef exec chef generate repo
```
This should automatically use the proper binaries path and gems path installed
with chefdk.

Finally, clone this repo somewhere locally and change to its directory.

Once you're in the directory, simply run:
```
vagrant up
```
And vagrant should do the rest.  Note that if you don't already have it installed,
vagrant will either attempt to download the box "ubuntu-12.04" or if it can't
find it, it will throw an error requesting you find one and add it.  You can find
urls for vagrant boxes @ http://vagrantbox.es.  Simply copy the url and run:
```
vagrant box add ubuntu-12.04 <ubuntu 12.04 box url>
```
Then rerun `vagrant up` and it should init a new box off of your image this time.

<!-- If the process terminates successfully, you're
ready to ssh in and configure your server.  Run:
```
vagrant ssh
```

Now that you're logged in, you need to install opscode-manage and configure your
new server.

vagrant@<your_hostname>:~$ sudo -->


## License and Authors

Author:: Patrick Armitage
