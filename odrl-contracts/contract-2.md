# Contract 2 - Usage allowed for service delivery + receive a copy of service data

## Assumptions
- Only usage for the the specified purpose, `dpv:ServiceDelivery`, is allowed.
- In GDPR equivalent jurisdictions, all purposes not mentioned are prohibited - this is also reflected in the chosen conflict resolution strategy, i.e., [odrl:perm](https://www.w3.org/ns/odrl/2/perm).
- In non-GDPR equivalent jurisdictions, all purposes beyond service delivery would be allowed unless they are explicitly prohibited - as such the non-GDPR variant must have a permission for service delivery and a prohibition for every purpose which is not service delivery.
- Assumes that the data in question is accessible at an IRI, e.g., `http://example.org/alice-data`.
- Assumes that the individual issuing the policy is identifiable through an IRI, e.g., `http://example.org/alice`.
- **[TO DISCUSS]** Current action being restricted is `odrl:use` - we could also use `dpv:Processing` instead to cover more ground.
- **[TO DISCUSS]** For the 'receive a copy of service data' obligation, we need to check which term form dpv better aligns -- using the high-level `dpv:Disclose` for now to cover more ground.
- **[TO DISCUSS]** Currently assuming that the service data in question is available somewhere at `http://example.org/service-data` but I believe the best approach would be to say that the asset of the user policy is something like `dpv:ServiceData` and only point towards the exact point where data is stored in the final signed agreement.

## User Policy -- GDPR variant

```ttl
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX odrl: <http://www.w3.org/ns/odrl/2/>
PREFIX dpv-odrl: <https://w3id.org/dpv/mappings/odrl#>
PREFIX dpv: <https://w3id.org/dpv#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

<http://example.org/contract-2-gdpr> a odrl:Offer ;
    odrl:uid <http://example.org/contract-2-gdpr> ;
    odrl:profile <https://w3id.org/dpv/mappings/odrl> ;
    dcterms:description "Usage allowed for service delivery and the user receives a copy of service data.";
    odrl:conflict odrl:perm ;
    odrl:permission <http://example.org/contract-2-gdpr-permission> ;
    odrl:obligation <http://example.org/contract-2-gdpr-obligation> .

<http://example.org/contract-2-gdpr-permission> a odrl:Permission ;
    odrl:action odrl:use ;
    odrl:target <http://example.org/alice-data> ;
    odrl:assigner <http://example.org/alice> ;
    odrl:constraint <http://example.org/contract-2-gdpr-permission-purpose> .

<http://example.org/contract-2-gdpr-permission-purpose> a odrl:Constraint ;
    odrl:leftOperand dpv-odrl:Purpose ;
    odrl:operator odrl:eq ;
    odrl:rightOperand dpv:ServiceDelivery .

<http://example.org/contract-2-gdpr-obligation> a odrl:Duty ;
    odrl:action dpv-odrl:Disclose ;
    odrl:target <http://example.org/service-data> ;
    odrl:assigner <http://example.org/alice> .
```

## User Policy -- non-GDPR variant

```ttl
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX odrl: <http://www.w3.org/ns/odrl/2/>
PREFIX dpv-odrl: <https://w3id.org/dpv/mappings/odrl#>
PREFIX dpv: <https://w3id.org/dpv#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

<http://example.org/contract-2-non-gdpr> a odrl:Offer ;
    odrl:uid <http://example.org/contract-2-non-gdpr> ;
    odrl:profile <https://w3id.org/dpv/mappings/odrl> ;
    dcterms:description "Usage allowed for service delivery and the user receives a copy of service data.";
    odrl:conflict odrl:perm ;
    odrl:permission <http://example.org/contract-2-non-gdpr-permission> ;
    odrl:prohibition <http://example.org/contract-2-non-gdpr-prohibition> ;
    odrl:obligation <http://example.org/contract-2-non-gdpr-obligation> .

<http://example.org/contract-2-non-gdpr-permission> a odrl:Permission ;
    odrl:action odrl:use ;
    odrl:target <http://example.org/alice-data> ;
    odrl:assigner <http://example.org/alice> ;
    odrl:constraint <http://example.org/contract-2-non-gdpr-permission-purpose> .

<http://example.org/contract-2-non-gdpr-permission-purpose> a odrl:Constraint ;
    odrl:leftOperand dpv-odrl:Purpose ;
    odrl:operator odrl:eq ;
    odrl:rightOperand dpv:ServiceDelivery .

<http://example.org/contract-2-non-gdpr-prohibition> a odrl:Prohibition ;
    odrl:action odrl:use ;
    odrl:target <http://example.org/alice-data> ;
    odrl:assigner <http://example.org/alice> ;
    odrl:constraint <http://example.org/contract-2-non-gdpr-prohibition-purpose> .

<http://example.org/contract-2-non-gdpr-prohibition-purpose> a odrl:Constraint ;
    odrl:leftOperand dpv-odrl:Purpose ;
    odrl:operator odrl:neq ;
    odrl:rightOperand dpv:ServiceDelivery .

<http://example.org/contract-2-non-gdpr-obligation> a odrl:Duty ;
    odrl:action dpv-odrl:Disclose ;
    odrl:target <http://example.org/service-data> ;
    odrl:assigner <http://example.org/alice> .
```