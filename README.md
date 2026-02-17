Zcash Integration Tests
<img align="right" width="120" height="80" src="doc/imgs/logo.png">
===========

This repository hosts integration tests and associated CI infrastructure for the
Zcash ecosystem. The following tests are provided:

- Functional tests in Python of [`zebrad`], [`zainod`], and [`zallet`], using
  regtest mode and primarily their JSON-RPC interfaces.

The functional tests and CI workflows were originally part of the [`zcashd`]
codebase, with the Python test framework (and some of the tests) inherited from
[Bitcoin Core].

[`zebrad`]: https://github.com/ZcashFoundation/zebra
[`zainod`]: https://github.com/zingolabs/zaino
[`zallet`]: https://github.com/zcash/wallet
[`zcashd`]: https://github.com/zcash/zcash
[Bitcoin Core]: https://github.com/bitcoin/bitcoin

## Getting Started

### Running the tests locally

- Clone the repository.
- Build `zebrad`, `zainod`, and `zallet` binaries, and place them in a folder
  `./src/` under the repository root.
- `python3 -m venv venv`
- `. venv/bin/activate`
- `pip3 install asyncio base58 toml`
- `./qa/zcash/full_test_suite.py`

See [the README for the functional tests][qa/README.md] for additional usage
information.

### Writing tests

- For new tests:
  - Add a new file `NEW_TEST.py` to the `qa/rpc-tests` folder.
  - Update `qa/pull-tester/rpc-tests.py`, adding a new entry `'NEW_TEST.py',` to
    the `BASE_SCRIPTS` array (either at the end of the array, or in the
    appropriate position based on how long the test takes to run).
- Write your test (either new from scratch, or making changes to an existing
  test as appropriate).
- Open a pull request with your changes.

Participation in the Zcash project is subject to a
[Code of Conduct](code_of_conduct.md).

License
-------

For license information see the file [COPYING](COPYING).
