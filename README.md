flojson
=======

Package flojson implements the Florincoin JSON-RPC API.  
This is a fork of btcjson by Conformal.
Package flojson and btcjson are licensed under the liberal ISC license.

The original package btcjson is one of the core packages from btcd, an alternative full-node
implementation of bitcoin which is under active development by Conformal.
Although it was primarily written for btcd, this package has intentionally been
designed so it can be used as a standalone package for any projects needing to
communicate with a bitcoin client using the json rpc interface.

## JSON RPC

Bitcoin and its desecndants provide an extensive API call list to control bitcoind or
bitcoin-qt through json-rpc.  These can be used to get information
from the client or to cause the client to perform some action.

The general form of the commands are:

```JSON
	{"jsonrpc": "1.0", "id":"test", "method": "getinfo", "params": []}
```

btcjson provides code to easily create these commands from go (as some
of the commands can be fairly complex), to send the commands to a
running bitcoin rpc server, and to handle the replies (putting them in
useful Go data structures).

## Sample Use

```Go
	msg, err := btcjson.CreateMessage("getinfo")
	reply, err := btcjson.RpcCommand(user, password, server, msg)
```

## Documentation

Full `go doc` style documentation for the project can be viewed online without
installing this package by using the GoDoc site
[here](http://godoc.org/github.com/metacoin/flojson).

You can also view the documentation locally once the package is installed with
the `godoc` tool by running `godoc -http=":6060"` and pointing your browser to
http://localhost:6060/pkg/github.com/metacoin/flojson

## Installation

```bash
$ go get github.com/conformal/btcjson
```

## TODO

- Add data structures for remaining commands.
- Increase test coverage to 100%.
- Add https support.

## GPG Verification Key

All official release tags are signed by Conformal so users can ensure the code
has not been tampered with and is coming from Conformal.  To verify the
signature perform the following:

- Download the public key from the Conformal website at
  https://opensource.conformal.com/GIT-GPG-KEY-conformal.txt

- Import the public key into your GPG keyring:
  ```bash
  gpg --import GIT-GPG-KEY-conformal.txt
  ```

- Verify the release tag with the following command where `TAG_NAME` is a
  placeholder for the specific tag:
  ```bash
  git tag -v TAG_NAME
  ```

## License

Package btcjson is licensed under the liberal ISC License.
