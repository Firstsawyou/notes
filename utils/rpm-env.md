# RPM for CentOS 7

Environment installation of fpm.

## initialize fpm environment

```shell
# install package centos-release-scl available in CentOS repository
yum install centos-release-scl

# install `ruby23` and `ruby-devel`
yum install -y rh-ruby23 rh-ruby23-ruby-devel.x86_64

# start using software collections
scl enable rh-ruby23 bash

# install dependencies for gem
yum install -y git make autoconf automake libtool pcre-devel gcc-c++ rubygems gcc rpm-build lua-devel cmake3

# install fpm with gem
gem install --no-ri --no-rdoc fpm
```
