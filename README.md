# TYPO3 Vagrant

A Vagrant file to get you up and running with TYPO3 in a few minutes.


## Requirements

* Oracle VirtualBox
* Vagrant (of course)
* vagrant-hostmanager plugin to easily access the virtual machine using domain names
* Ruby (comes pre-installed on OS X)
* RubyGems - the Ruby package manager (also comes with OS X) 
* Librarian-Chef to resolve dependencies of Chef cookbooks we use to provision the virtual machine
* Opscode Chef (knowledge optional but for sure nice to have)


## Setup

1. Download and install VirtualBox
2. Download and install Vagrant - the most recent version should be fine
3. Install the vagrant-hostmanager plugin: In a terminal execute `vagrant plugin install vagrant-hostmanager` 
4. Use RubyGems to install Librarian Chef by executing the following command a terminal: `gem install librarian-chef`
5. Check out your project from source control
6. Let Librarian fetch all the Chef cookbooks and their dependencies by executing `librarian-chef install`
7. Now you are ready to `vagrant up` in your project directory


## Contributing

1. Fork the repository on Github
2. Create a named feature branch (like `feature_x`)
3. Write your change
4. Write tests for your change (if applicable)
5. Run the tests, ensuring they all pass
6. Submit a Pull Request using Github


## License and Authors

Authors: [Ingo Renner](http://github.com/irnnr) [(@irnnr)](http://twitter.com/irnnr)

Copyright: 2013, Ingo Renner

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
