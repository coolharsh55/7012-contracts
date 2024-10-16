# 7012-contracts
Experimental contracts for IEEE P7012 based on ODRL and DPV

## Summary of modelled contracts

| Contract # | Rule        | Conflict Strategy | Purpose                            | ODRL Policy                                  |
|------------|-------------|-------------------|------------------------------------|----------------------------------------------|
| 0          | Prohibition | `perm`            |                                    | [contract-0](./odrl-contracts/contract-0.md) |
| 1-GDPR     | Permission  | `perm`            | equal to `dpv:ServiceDelivery`     | [contract-1](./odrl-contracts/contract-1.md) |
| 1-non-GDPR | Permission  | `perm`            | equal to `dpv:ServiceDelivery`     | [contract-1](./odrl-contracts/contract-1.md) |
| 1-non-GDPR | Prohibition | `perm`            | not equal to `dpv:ServiceDelivery` | [contract-1](./odrl-contracts/contract-1.md) |

## Additional context

- Individuals' policies are modelled as `odrl:Offer` since they represent the conditions of data use that any recipients of the policy must adhere to be able to use said data
- Organisations/other individuals looking to use said data must issue an `odrl:Request` that matches the offer of the individual
- Once an agreement is settled, the conditions of the contract are consolidated in an `odrl:Agreement`
- This follows previous work done [here](https://content.iospress.com/articles/semantic-web/sw243583) and also aligns with the [formal semantics of ODRL](https://w3c.github.io/odrl/formal-semantics/)

## Action points

- `dpv:ServiceDelivery` is not yet in DPV
- `https://w3id.org/dpv/mappings/odrl` mapping is not yet online but the necessary bits will be soon 