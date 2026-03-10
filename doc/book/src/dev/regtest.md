# Regtest Mode

Regtest (regression test) mode runs a local Zcash network where blocks are
generated on demand. This gives tests full control over block timing and chain
state.

The draft [ZIP for regtest mode](https://github.com/zcash/zips/pull/986)
provides the formal specification.

## Key constants

| Parameter | Value |
|---|---|
| Initial block subsidy | 12.5 ZEC |
| Post-Blossom block subsidy | 6.25 ZEC |
| Halving interval (pre-Blossom) | 144 blocks |
| Coinbase maturity | 100 blocks |

## Network upgrade activation

Zebra activates Overwinter through Canopy at block height 1 by default. Tests
that need NU5 or later upgrades require explicit `-nuparams` configuration.

## Interacting with nodes during a test

To inspect node state mid-test, you can pause execution (e.g. with a debugger
breakpoint or `time.sleep()`) and issue RPC calls against the node's RPC port.
Each node's RPC port is logged at startup.
