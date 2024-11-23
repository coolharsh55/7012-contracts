# 7012-contracts
Experimental contracts for IEEE P7012 based on ODRL and DPV

## Summary of modelled contracts

**Table needs to be updated**

| Contract # | Rule        | Conflict Strategy | Action              | Purpose                                                               | ODRL Policy                                  |
|------------|-------------|-------------------|---------------------|-----------------------------------------------------------------------|----------------------------------------------|
| 0          | Prohibition | `perm`            | `odrl:use`          |                                                                       | [contract-0](./odrl-contracts/contract-0.md) |
| 1-GDPR     | Permission  | `perm`            | `odrl:use`          | equal to `dpv:ServiceProvision`                                        | [contract-1](./odrl-contracts/contract-1.md) |
| 1-non-GDPR | Permission  | `perm`            | `odrl:use`          | equal to `dpv:ServiceProvision`                                        | [contract-1](./odrl-contracts/contract-1.md) |
| 1-non-GDPR | Prohibition | `perm`            | `odrl:use`          | not equal to `dpv:ServiceProvision`                                    | [contract-1](./odrl-contracts/contract-1.md) |
| 2-GDPR     | Permission  | `perm`            | `odrl:use`          | equal to `dpv:ServiceProvision`                                        | [contract-2](./odrl-contracts/contract-2.md) |
| 2-GDPR     | Duty        | `perm`            | `dpv-odrl:Disclose` |                                                                       | [contract-2](./odrl-contracts/contract-2.md) |
| 2-non-GDPR | Permission  | `perm`            | `odrl:use`          | equal to `dpv:ServiceProvision`                                        | [contract-2](./odrl-contracts/contract-2.md) |
| 2-non-GDPR | Prohibition | `perm`            | `odrl:use`          | not equal to `dpv:ServiceProvision`                                    | [contract-2](./odrl-contracts/contract-2.md) |
| 2-non-GDPR | Duty        | `perm`            | `dpv-odrl:Disclose` |                                                                       | [contract-2](./odrl-contracts/contract-2.md) |
| 3-GDPR     | Permission  | `perm`            | `odrl:use`          | is any of `dpv:ServiceProvision` or `dpv:ServiceImprovementAnalytics`  | [contract-3](./odrl-contracts/contract-3.md) |
| 3-non-GDPR | Permission  | `perm`            | `odrl:use`          | is any of `dpv:ServiceProvision` or `dpv:ServiceImprovementAnalytics`  | [contract-3](./odrl-contracts/contract-3.md) |
| 3-non-GDPR | Prohibition | `perm`            | `odrl:use`          | is none of `dpv:ServiceProvision` or `dpv:ServiceImprovementAnalytics` | [contract-3](./odrl-contracts/contract-3.md) |

## Additional context

- Individuals' policies are modelled as `odrl:Offer` since they represent the conditions of data use that any recipients of the policy must adhere to be able to use said data
- Organisations/other individuals looking to use said data must issue an `odrl:Request` that matches the offer of the individual
- Once an agreement is settled, the conditions of the contract are consolidated in an `odrl:Agreement`
- This follows previous work done [here](https://content.iospress.com/articles/semantic-web/sw243583) and also aligns with the [formal semantics of ODRL](https://w3c.github.io/odrl/formal-semantics/)

## Action points

- `dpv:ServiceData` is not yet in DPV
- FirstPartyTracking, ThirdPartyTracking -> Tracking: all three missing from DPV
- TrackingData & ProfilingData missing from DPV
- FirstPartyProfiling & ThirdPartyProfiling missing from DPV
- AnonymousServiceData missing from DPV

- `https://w3id.org/dpv/mappings/odrl` mapping is not yet online but the necessary bits will be soon 