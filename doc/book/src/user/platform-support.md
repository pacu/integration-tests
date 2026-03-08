# Platform Support

Support for testing different platforms (build "targets" and operating systems) is
governed by the [Platform Policy](../dev/platform-policy.md).

Tested platforms can be thought of as "guaranteed to work". Automated testing ensures that
each tested platform builds and passes tests after each change to the upstream binaries.

The following table contains the set of tested platforms that binary providers can make
use of as part of their own testing workflows.

"End of Support" dates are the latest currently-known date after which the platform will
be removed. These dates are subject to change.

| target                  | OS           | End of Support | Notes |
| ----------------------- | ------------ | -------------- | ----- |
| `x86_64-pc-linux-gnu`   | Debian 11    | June 2026      |
|                         | Debian 12    | June 2028      |
|                         | Ubuntu 22.04 | April 2027     |
|                         | Ubuntu 24.04 |
| `x86_64-w64-mingw32`    | Windows      |                | 64-bit MinGW |
| `x86_64-apple-darwin16` | macOS 10.14+ |
| `aarch64-linux-gnu`     | ARM64 Linux  |
