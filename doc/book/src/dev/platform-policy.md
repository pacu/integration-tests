# Platform Policy

## General

The continuous integration checks in this repository ensure that tested platforms will
always build and pass tests. These platforms place work on Zcash developers as a whole, to
avoid breaking the platform. The broader Zcash community may also feel more inclined to
support tested platforms in their downstream uses of `zebrad`, `zainod`, or `zallet`
(though they are not obligated to do so). Thus, tested platforms require commensurate and
ongoing efforts from the maintainers of the platform, to demonstrate value and to minimize
any disruptions to ongoing Zcash development.

This policy defines the requirements for accepting a proposed platform into the set of
tested platforms.

While these criteria attempt to document the policy, that policy still involves human
judgment. Platforms must fulfill the spirit of the requirements as well, as determined by
the judgment of the approving reviewers. Reviewers and team members evaluating platforms
and platform-specific patches should always use their own best judgment regarding the
quality of work, and the suitability of a platform for the Zcash project. Neither this
policy nor any decisions made regarding platforms shall create any binding agreement or
estoppel by any party.

For a list of all supported platforms, see [Platform Support](../user/platform-support.md).

The availability of a platform in releases of Zcash ecosystem software is not a hard
stability guarantee about the future availability of that platform. Tested platforms are
a commitment to the support of a platform, and we will take that commitment and potential
disruptions into account when evaluating the potential removal of a platform that has been
part of a stable release of Zcash ecosytem software. The addition or removal of a platform
will not generally affect existing stable releases, only current development and future
releases.

In this policy, the words "MUST" and "MUST NOT" specify absolute requirements that a
platform must meet to qualify. The words "SHOULD" and "SHOULD NOT" specify requirements
that apply in almost all cases, but for which the approving teams may grant an exception
for good reason. The word "MAY" indicates something entirely optional, and does not
indicate guidance or recommendations. This language is based on
[IETF RFC 2119](https://tools.ietf.org/html/rfc2119).

## Tested platform policy

The Zcash developers guarantee that a tested platform builds and passes all tests, and
will reject patches that fail to build or pass the test suite on a platform. Thus, we
place requirements that ensure the platform will not block forward progress of the Zcash
project.

A proposed new platform MUST be reviewed and approved by the Zcash core team based on
these requirements.

In addition, the Zcash infrastructure team MUST approve the integration of the platform
into Continuous Integration (CI), and the CI-related requirements. This review and
approval MAY take place in a PR adding the platform to CI, or simply by an infrastructure
team member reporting the outcome of a team discussion.

- The platform MUST provide documentation for the Zcash community explaining how to build
  for the platform, using cross-compilation if possible. If the platform supports running
  binaries, or running tests (even if they do not pass), the documentation MUST explain
  how to run such binaries or tests for the platform, using emulation if possible or
  dedicated hardware if necessary.
- The platform MUST have a designated team of developers (the "platform maintainers")
  supporting it, without the need for a paid support contract.
- The platform MUST NOT place undue burden on Zcash developers not specifically concerned
  with that platform. Zcash developers are expected to not gratuitously break a tested
  platform, but are not expected to become experts in every tested platform.
- The platform MUST have substantial, widespread interest within the Zcash community,
  and MUST serve the ongoing needs of multiple production users of Zcash across multiple
  organizations or projects. These requirements are subjective. A tested platform MAY be
  removed if it becomes obsolete or no longer meets this requirement.
- The platform MUST build and pass tests reliably in CI, for all components that this
  repo's CI marks as mandatory.
- Building the platform and running the test suite for the platform MUST NOT take
  substantially longer than other platforms, and SHOULD NOT substantially raise the
  maintenance burden of the CI infrastructure.
- The platform MUST NOT have a hard requirement for signed, verified, or otherwise
  "approved" binaries. Developers MUST be able to build, run, and test binaries for the
  platform on systems they control, or provide such binaries for others to run. (Doing so
  MAY require enabling some appropriate "developer mode" on such systems, but MUST NOT
  require the payment of any additional fee or other consideration, or agreement to any
  onerous legal agreements.)

A platform MAY be removed if it no longer meets these requirements.
