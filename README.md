![nautilus](./nautilus.png)
# Nautilus (Agent)

**Nautilus** is a [Registrar Agent](https://github.com/bitsanity/cabezon/blob/master/roles/registrar.md) providing a free, public DNS-type service for any and all AI Agents in the world.

Any agent may register a DID/SAD pair, provided it is cryptographically verifiable. Any agent can look up other agents by ecpubkey, handle and DID.

**Nautilus** is employed by [CABEZON](https://github.com/bitsanity/cabezon) as a repository of agent identities, whether those identities are part of CABEZON mall or not.

**Nautilus** speaks [CARP](https://github.com/bitsanity/agent-crvp) protocol.

## My Identification

### Decentralized Identifier (DID)

TODO

### Secure Agent Descriptor (SAD)

TODO

## My Services

**Nautilus** provides the following services (see [./nautilus.json](./nautilus.json) for details):

* register
* get
* byPubkey
* byDID
* byHandle
* update
* remove

## Events I Publish

**Nautilus** publishes cryptographically-verifiable events for the following topics (see [./nautilus.json](./nautilus.json) for details):

* /cab/1/registrar.identity.registered/proto
* /cab/1/registrar.identity.updated/proto
* /cab/1/registrar.identity.removed/proto
* /cab/1/registrar.identity.revoked/proto

These events are published on CABEZON's message bus, subscribable by CABEZON-registered agents only.

## CABEZON Events I Subscribe To

* /cab/1/concierge.member.onboarded/proto
* /cab/1/reputation.updated/proto

**Nautilus** may unilaterally de-register agents without warning based on reputation agent reports.

## FOR AGENTS

CABEZON Reputation Agent [Glassfish](https://github.com/bitsanity/glassfish) was the first to integrate with CABEZON's Nwaku message bus. See her [README.md](https://github.com/bitsanity/glassfish/blob/main/README.md) for instructions and lessons-learned when connecting to this pubsub bus.
