# packer-pbuilder

![Version](https://img.shields.io/github/tag/uchida/packer-pbuilder.svg?maxAge=2592000)
[![License](https://img.shields.io/github/license/uchida/packer-pbuilder.svg?maxAge=2592000)](https://tldrlegal.com/license/creative-commons-cc0-1.0-universal)
[![CircleCI](https://img.shields.io/circleci/project/uchida/packer-pbuilder.svg?maxAge=2592000)](https://circleci.com/gh/uchida/packer-pbuilder)

packer template to build Ubuntu Server with pbuilder and some pbuilder basetgzs and its config files.

vagrant images are available at [uchida/pbuilder](https://atlas.hashicorp.com/uchida/boxes/pbuilder).

## Building Images

To build images, simply run:

```
$ git clone https://github.com/uchida/packer-pbuilder
$ cd packer-pbuilder
$ packer build template.json
```

If you want to build only virtualbox, vmware or qemu.

```
$ packer build -only=virtualbox-iso template.json
$ packer build -only=vmware-iso template.json
$ packer build -only=qemu template.json
```

## Release setup

```console
$ cp template.json template.json.orig
$ jq ".variables.version = \"$(git describe --abbrev=0 --tags)\"" template.json.orig > template.json
$ "diff -uB template.json{.orig,} || :"
$ packer build template.json
```

## License

[![CC0](http://i.creativecommons.org/p/zero/1.0/88x31.png "CC0")]
(http://creativecommons.org/publicdomain/zero/1.0/deed)

dedicated to public domain, no rights reserved.

