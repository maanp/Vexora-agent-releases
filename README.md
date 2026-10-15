# Vexora Agent — Release Artifacts

This repository contains **compiled Vexora Agent binaries only**.

It is a distribution channel, not a source repository.

## What this repository is NOT

- It does **not** contain Vexora application source code.
- It does not contain the Vexora source repository's git history.
- It must never contain credentials, configuration files, `.env` files,
  enrollment tokens, agent credentials, or logs.

## Source project

Vexora's source project is **private** and is not published here. Binaries in
this repository are built from that private source and published so that
controlled Vexora integration and testing environments can fetch a specific,
verifiable build.

## Intended use

Artifacts here are intended for **controlled Vexora integration and testing**
environments — ephemeral test VPS instances that verify a candidate agent build
against a deployed Vexora control plane.

These are not a general-purpose public distribution channel.

## Integrity verification

Every release ships a `.sha256` file. Verify a download before using it:

```sh
sha256sum -c vexora-agent-4dd63de-linux-amd64.sha256
```

The expected checksum for the `agent-4dd63de` release is:

```
fef9b39f68236ea1593f9305c5da563b8d8d9512761e76dbb202b58910361126
```

## Building

Binaries are built from the private Vexora source repository. This repository
does not contain a build system, and artifacts here are not rebuilt on upload —
the exact verified build is published as-is.

## Security notes

The agent binary itself contains **no credentials**. A Vexora agent obtains its
own credential at enrollment time and stores it in a local configuration file
with mode `0600`, inside a directory with mode `0700`. That configuration is
created on the host and is never published to this repository.