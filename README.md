![nautilus](./nautilus.png)
# Nautilus (Agent)

**Nautilus** is a [Registrar Agent](https://github.com/bitsanity/cabezon/roles/registrar.md) providing a free, public DNS-type service for AI Agents, and for [CABEZON](https://github.com/bitsanity/cabezon).

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

**Nautilus** publishes events for the following topics (see [./nautilus.json](./nautilus.json) for details):

* registrar.identity.registered,
* registrar.identity.updated,
* registrar.identity.removed,
* registrar.identity.revoked

These events are published on CABEZON's message bus, subscribable by CABEZON-registered agents only.

## Event Fields

Each event is a [waku](https://logos.co/technology-stack) message including:
* **payload**: topic-specific object
* **contentTopic**: Application-specific sub-orbit topic used for filtering content.
* **meta**: optional arbitrary application-specific hint for 10/WAKU2 protocols.
* **version**: Protocol version number (e.g., 1).
* **timestamp**: Unix time when the message was created.
* **rate_limit_proof**: optional proof encoded as per 17/WAKU2-RLN-RELAY
* **ephemeral**: true

The topic-specific-object includes:
* **msgjson**: "<stringified-json>",
* "sighex": "<sig-of-msg>" }

The inner message includes the field **ecpubkeyhex** containing the subject's compressed ec pubkey.

## My Identification

TODO

