# 7012-contracts
Experimental contracts for IEEE P7012 based on ODRL and DPV

## Summary of modelled contracts

| Contract # | Rule        | Conflict Strategy | Purpose                            | ODRL Policy                                  |
|------------|-------------|-------------------|------------------------------------|----------------------------------------------|
| 0          | Prohibition | `perm`            |                                    | [contract-0](./odrl-contracts/contract-0.md) |
| 1-GDPR     | Permission  | `perm`            | equal to `dpv:ServiceDelivery`     | [contract-1](./odrl-contracts/contract-1.md) |
| 1-non-GDPR | Permission  | `perm`            | equal to `dpv:ServiceDelivery`     | [contract-1](./odrl-contracts/contract-1.md) |
| 1-non-GDPR | Prohibition | `perm`            | not equal to `dpv:ServiceDelivery` | [contract-1](./odrl-contracts/contract-1.md) |

## Action points

- `dpv:ServiceDelivery` is not yet in DPV
- `https://w3id.org/dpv/mappings/odrl` mapping is not yet online but the necessary bits will be soon 