# Verifiable Credentials Specification
__Version 1.3.0__

[Attribute Sets](../DSNP/AttributeSets.md) and [Attestation](../ActivityContent/Associated/Attachments.md#attestation) attachments shared via DSNP reference data documents containing Verifiable Credentials and related objects.
For DSNP purposes, certain restrictions and extensions are applied to the base World Wide Web Consortium (W3C) specification documents noted below.
When there are DSNP extensions, they are guaranteed to use non-colliding terms.

It is anticipated that these W3C specifications will evolve, and applications interacting with Verifiable Credentials, Schemas, and DIDs via DSNP are encouraged to be as flexible as possible in their syntax support as new versions and supporting software libraries become available.
Therefore, compatibility with the following versions and specifications should be construed as the minimal level of support required to ensure interoperability between DSNP applications.

## Compatibility

Current usage with DSNP relies on the following specifications:

| Specification | Version/Status | Relevant JSON-LD `@context` Values |
| --- | --- | --- |
 | Verifiable Credentials Data Model | [1.1 (W3C Recommendation)](https://www.w3.org/TR/vc-data-model-1.1)<br>[2.0 (W3C Candidate Recommendation Draft 15 September 2024)](https://www.w3.org/TR/2024/CRD-vc-data-model-2.0-20240915/) | `https://www.w3.org/2018/credentials/v1`<br>`https://www.w3.org/ns/credentials/v2` |
 | Verifiable Credential Data Integrity | [1.0 (W3C Candidate Recommendation Draft 16 September 2024)](https://www.w3.org/TR/2024/CRD-vc-data-integrity-20240916/) | `https://w3id.org/security/data-integrity/v2`<br>`https://w3id.org/security/multikey/v1` |
 | Verifiable Credentials JSON Schema | [(W3C Candidate Recommendation Draft 12 September 2024)](https://www.w3.org/TR/2023/CRD-vc-json-schema-20240912/) | |
 | Decentralized Identifiers (DIDs) | [1.0 (W3C Recommendation 19 July 2022)](https://www.w3.org/TR/2022/REC-did-core-20220719/) | `https://www.w3.org/ns/did/v1` |

### Cryptography

The Data Integrity specification provides a generic format for expressing cryptographic proofs, where the detailed representation of each data item is defined in individual cryptosuites.
DSNP compliant applications MUST support the following cryptosuites, which correspond to the allowed algorithms for the DSNP User Data item [`assertionMethodPublicKeys`](../DSNP/Types/PublicKeyUserData.md#allowed-key-types):

| Specification | Version/Status | Multikey codec |
| --- | --- | --- |
| Data Integrity EdDSA Cryptosuites | [1.0 (W3C Candidate Recommendation Draft 16 September 2024)](https://www.w3.org/TR/2024/CRD-vc-di-eddsa-20240924/) | `ed25519-pub` |


## DSNP Usage Details

DSNP incorporates the following W3C JSON-LD types.
See the individual pages for details of restrictions to and extensions on each type.

| Name | Since DSNP Version |
| --- | --- |
 | [Verifiable Credential](./Types/VerifiableCredential.md) | 1.3 |
 | [Verifiable Credential Schema](./Types/VerifiableCredentialSchema.md) | 1.3 |
 | [DID](./Types/DID.md) | 1.3 |

## Libraries

| Name | Language(s) |
| --- | --- |
| [LibertyDSNP/dsnp-verifiable-credentials](https://github.com/LibertyDSNP/dsnp-verifiable-credentials) | JavaScript/TypeScript |
| [LibertyDSNP/dsnp-did-resolver](https://github.com/LibertyDSNP/dsnp-did-resolver) | JavaScript/TypeScript |

<!--- Uncomment for pre-release changes and prefix the version with `pre-[next version]`
## Prerelease Changelog

- [DIP-xxx](https://github.com/LibertyDSNP/spec/issues/xxx) Name of Feature
--->

## Releases

| Version | Description | Release Date | Changelog |
| --- | --- | --- | --- |
| 1.3.0 | DIP-257 | 2024-09-17 | [Changelog](https://github.com/LibertyDSNP/spec/releases/tag/VerifiableCredentials-v1.3.0) |

## Non-Normative

### Additional Fields

DSNP application developers may choose to support more of the relevant JSON-LD vocabularies from the specifications above as long as doing so does not conflict with this specification, but should note that other conforming applications may not recognize those additions.
Implementers who extend their support for Verifiable Credentials objects beyond the subset defined here do so at their own risk.

### Verifiable Presentations

[Verifiable Presentations](https://www.w3.org/TR/vc-data-model-2.0/#verifiable-presentations) combine one or more Verifiable Credentials in a single document.
These might be existing Verifiable Credentials, whether or not previously published, or new Verifiable Credentials derived from non-public source credentials using methods like zero-knowledge proofs.
At this time, Verifiable Presentations are not directly tied to DSNP content or announcements.
However, application and service providers may be interested in implementing functionality using Verifiable Presentations with DSNP Verifiable Credentials.
Applications are encouraged to follow the verification guidelines for DSNP Verifiable Credentials even when encountering those credentials as part of a Verifiable Presentation.
