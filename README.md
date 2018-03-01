outlyer-agent Puppet Module
============================
This is a puppet module that installs the outlyer-agent on a host. It makes use of the puppetlabs apt module and the outlyer.com public yum and apt repositories.

Requirements
------------
* Tested on puppet 3.7.3
* Puppetlabs-apt module

Platforms
---------
* Ubuntu 12.04, 14.04, 16.04
* Debain 8, 9
* Rhel/Centos >= 6

Usage
-----
If you don't already have it, import the puppetlabs-apt module to your puppet repository

`#> puppet module install puppetlabs-apt --version 1.7.0`

And import this outlyer-agent module. Since the module only exists on GitHub we manually download the source and install it to the users modulepath. The REVISION can be a commit, branch or tag.

```
#> cd [MODULEPATH]
#> curl -L https://github.com/outlyerapp/dataloop-puppet/archive/[REVISION].tar.gz | sudo tar xz
#> mv outlyer-puppet-[REVISION] outlyer_agent
```

Add the outlyer-agent module to your node's run list and pass in the agent_key for your Outlyer account so that your servers can communicate back.

```
class { 'outlyer_agent': 
  agent_key => 'fa970ce7-de56-4b98-915f-bb7d828c68d2'
}
```


Testing
-------
Testing for this module has been setup with Librarian-puppet and Test-Kitchen utilising vagrant as the machine provider.

Clone the repository, install the Gems (gem file to come), update the api_key in _manifests/test_site.pp_ and run kitchen test.

```
#> bundle install
#> kitchen test
```

Contributing
------------
Pull requests welcome.

License and Authors
-------------------
Author: Tom Ashley <tom.ashley@outlyer.com>

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
