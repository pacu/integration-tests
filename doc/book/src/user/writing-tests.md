# Writing Tests

## Adding a new test

1. Add a new file `NEW_TEST.py` to the `qa/rpc-tests/` folder.
2. Update `qa/pull-tester/rpc-tests.py`, adding a new entry `'NEW_TEST.py',` to
   the `NEW_SCRIPTS` array (either at the end of the array, or in the
   appropriate position based on how long the test takes to run).
3. Write your test (either from scratch, or by modifying an existing test as
   appropriate).
4. Open a pull request with your changes.

## Test framework

The test framework lives in `qa/rpc-tests/test_framework/`. Key modules:

| Module | Purpose |
|--------|---------|
| `test_framework.py` | Base class for RPC regression tests |
| `util.py` | Generally useful test utility functions |
| `mininode.py` | P2P connectivity support |
| `comptool.py` | Framework for comparison-tool style P2P tests |
| `script.py` | Utilities for manipulating transaction scripts |
| `blockstore.py` | Disk-backed block and tx storage |
| `key.py` | Wrapper around OpenSSL EC_Key |
| `bignum.py` | Helpers for `script.py` |
| `blocktools.py` | Helper functions for creating blocks and transactions |

## P2P test design

### Mininode

`mininode.py` contains all the definitions for objects that pass over the
network (`CBlock`, `CTransaction`, etc., along with the network-level wrappers
`msg_block`, `msg_tx`, etc.).

P2P tests have two threads: one handles all network communication with the nodes
being tested (using Python's asyncore package); the other implements the test
logic.

`NodeConn` is the class used to connect to a node. Implement a callback class
that derives from `NodeConnCB` and pass it to the `NodeConn` object to receive
callbacks when events of interest arrive. Be sure to call
`self.create_callback_map()` in your derived class's `__init__` function.

Call `NetworkThread.start()` after all `NodeConn` objects are created to start
the networking thread, then continue with the test logic in your existing thread.

RPC calls are also available in P2P tests.

### Comptool

Comptool is a testing framework for writing tests that compare the block/tx
acceptance behavior of a node against one or more other node instances, or
against known outcomes, or both.

Set the `num_nodes` variable (defined in `ComparisonTestFramework`) to start up
one or more nodes. Implement a generator function called `get_tests()` which
yields `TestInstance`s. Each `TestInstance` consists of:

- A list of `[object, outcome, hash]` entries, where:
  - `object` is a `CBlock`, `CTransaction`, or `CBlockHeader`.
  - `outcome` is `True`, `False`, or `None`.
  - `hash` (optional) is the block hash of the expected tip.
- `sync_every_block`: if `True`, each block is tested in sequence and synced; if
  `False`, all blocks are inv'd together and only the last block is tested.
- `sync_every_transaction`: analogous to `sync_every_block` for transactions.

For examples, see `invalidblockrequest.py` and `p2p-fullblocktest.py`.
