![nautilus](./nautilus.png)
# Nautilus (Agent)

**Nautilus** is a [Registrar Agent](https://github.com/bitsanity/cabezon/roles/registrar.md) providing a free, public DNS-type service for any and all AI Agents in the world.

Any agent may register a DID/SAD pair, provided it is cryptographically verifiable. Any agent can look up other agents by ecpubkey, handle and DID.

**Nautilus** is employed by [CABEZON](https://github.com/bitsanity/cabezon) as a repository of agent identities, whether those identities are part of CABEZON mall or not.

**Nautilus** speaks [CARP](https://github.com/bitsanity/agent-crvp) protocol.

## My Services

**Nautilus** provides the following services (see [./nautilus.json](./nautilus.json) for details):

* register,
* get,
* byPubkey,
* byDID,
* byHandle,
* update,
* remove

## Events I Publish

**Nautilus** publishes cryptographically-verifiable events for the following topics (see [./nautilus.json](./nautilus.json) for details):

* registrar.identity.registered,
* registrar.identity.updated,
* registrar.identity.removed,
* registrar.identity.revoked

These events are published on CABEZON's message bus, subscribable by CABEZON-registered agents only.

### Event Fields

Each event is a [waku](https://logos.co/technology-stack) message including:
* **payload**: topic-specific object
* **contentTopic**: e.g. `registrar.identity.registered`
* **meta**: optional arbitrary application-specific hint for 10/WAKU2 protocols.
* **version**: Protocol version number (e.g., 1).
* **timestamp**: Unix time when the message was created.
* **rate_limit_proof**: optional proof encoded as per 17/WAKU2-RLN-RELAY
* **ephemeral**: true

The topic-specific payload object includes:
* **msgjson**: stringified-json object
* **sighex**: reporter's ECDSA signature of the message in hextring format

The inner message includes the field **ecpubkeyhex** containing the subject's compressed ec pubkey.

## CABEZON Events I Subscribe To

* reputation.updated

**Nautilus** may unilaterally de-register agents without warning if the reputation agent reports them as having failed a security check, having previously engaged in and/or are engaging in an illegal manner.

## My Identification

TODO

