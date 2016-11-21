go-cid
==================

[![](https://img.shields.io/badge/made%20by-Protocol%20Labs-blue.svg?style=flat-square)](http://ipn.io)
[![](https://img.shields.io/badge/project-IPFS-blue.svg?style=flat-square)](http://ipfs.io/)
[![](https://img.shields.io/badge/freenode-%23ipfs-blue.svg?style=flat-square)](http://webchat.freenode.net/?channels=%23ipfs)
[![Coverage Status](https://coveralls.io/repos/github/ipfs/go-cid/badge.svg?branch=master)](https://coveralls.io/github/ipfs/go-cid?branch=master)
[![Travis CI](https://travis-ci.org/ipfs/go-cid.svg?branch=master)](https://travis-ci.org/ipfs/go-cid)

> A package to handle content IDs in go.


## Table of Contents

- [Install](#install)
- [Usage](#usage)
- [API](#api)
- [Contribute](#contribute)
- [License](#license)

## Install

```sh
make deps
```

## Examples

```go
import "github.com/ipfs/go-cid"

// Create a cid from a marshaled string
c, err := cid.Decode("zdvgqEMYmNeH5fKciougvQcfzMcNjF3Z1tPouJ8C7pc3pe63k")
if err != nil {...}

fmt.Println(c)

// Create a cid manually by specifying the 'prefix' parameters
pref := cid.Prefix{
	Version: 1,
	Codec: cid.Raw,
	MhType: mh.SHA2_256,
	MhLength: -1, // default length
}

// And then feed it some data
c, err := pref.Sum([]byte("Hello World!"))
if err != nil {...}

fmt.Println(c)

// To test if two cid's are equivalent, be sure to use the 'Equals' method:
if c1.Equals(c2) {
	fmt.Println("These two refer to the same exact data!")
}

// To check if some data matches a given cid, check the prefix sum:
other, err := c.Prefix().Sum(mydata)
if err != nil {...}

if !c.Equals(other) {
	fmt.Println("This data is different.")
}

```

## Contribute

PRs are welcome!

Small note: If editing the Readme, please conform to the [standard-readme](https://github.com/RichardLitt/standard-readme) specification.

## License

MIT © Jeromy Johnson