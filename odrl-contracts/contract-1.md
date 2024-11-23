# Contract 1 - Usage allowed for service provision

## Assumptions
- Only usage for the the specified purpose, `dpv:ServiceProvision`, is allowed.
- In GDPR equivalent jurisdictions, all purposes not mentioned are prohibited - this is also reflected in the chosen conflict resolution strategy, i.e., [odrl:perm](https://www.w3.org/ns/odrl/2/perm).
- In non-GDPR equivalent jurisdictions, all purposes beyond service delivery would be allowed unless they are explicitly prohibited - as such the non-GDPR variant must have a permission for service provision and a prohibition for every purpose which is not service provision.
- Assumes that the data in question is accessible at an IRI, e.g., `http://example.org/alice-data`.
- Assumes that the individual issuing the policy is identifiable through an IRI, e.g., `http://example.org/alice`.
- **[TO DISCUSS]** Current action being restricted is `odrl:use` - we could also use `dpv:Processing` instead to cover more ground.

## User Policy -- GDPR variant

```ttl
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX odrl: <http://www.w3.org/ns/odrl/2/>
PREFIX dpv-odrl: <https://w3id.org/dpv/mappings/odrl#>
PREFIX dpv: <https://w3id.org/dpv#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

<http://example.org/contract-1-gdpr> a odrl:Offer ;
    odrl:uid <http://example.org/contract-1-gdpr> ;
    odrl:profile <https://w3id.org/dpv/mappings/odrl> ;
    dcterms:description "Usage allowed for service provision.";
    odrl:conflict odrl:perm ;
    odrl:permission <http://example.org/contract-1-gdpr-permission> .

<http://example.org/contract-1-gdpr-permission> a odrl:Permission ;
    odrl:action odrl:use ;
    odrl:target <http://example.org/alice-data> ;
    odrl:assigner <http://example.org/alice> ;
    odrl:constraint <http://example.org/contract-1-gdpr-permission-purpose> .

<http://example.org/contract-1-gdpr-permission-purpose> a odrl:Constraint ;
    odrl:leftOperand dpv-odrl:Purpose ;
    odrl:operator odrl:eq ;
    odrl:rightOperand dpv:ServiceProvision .
```

## User Policy -- non-GDPR variant

```ttl
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX odrl: <http://www.w3.org/ns/odrl/2/>
PREFIX dpv-odrl: <https://w3id.org/dpv/mappings/odrl#>
PREFIX dpv: <https://w3id.org/dpv#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

<http://example.org/contract-1-non-gdpr> a odrl:Offer ;
    odrl:uid <http://example.org/contract-1-non-gdpr> ;
    odrl:profile <https://w3id.org/dpv/mappings/odrl> ;
    dcterms:description "Usage allowed for service provision.";
    odrl:conflict odrl:perm ;
    odrl:permission <http://example.org/contract-1-non-gdpr-permission> ;
    odrl:prohibition <http://example.org/contract-1-non-gdpr-prohibition> .

<http://example.org/contract-1-non-gdpr-permission> a odrl:Permission ;
    odrl:action odrl:use ;
    odrl:target <http://example.org/alice-data> ;
    odrl:assigner <http://example.org/alice> ;
    odrl:constraint <http://example.org/contract-1-non-gdpr-permission-purpose> .

<http://example.org/contract-1-non-gdpr-permission-purpose> a odrl:Constraint ;
    odrl:leftOperand dpv-odrl:Purpose ;
    odrl:operator odrl:eq ;
    odrl:rightOperand dpv:ServiceProvision .

<http://example.org/contract-1-non-gdpr-prohibition> a odrl:Prohibition ;
    odrl:action odrl:use ;
    odrl:target <http://example.org/alice-data> ;
    odrl:assigner <http://example.org/alice> ;
    odrl:constraint <http://example.org/contract-1-non-gdpr-prohibition-purpose> .

<http://example.org/contract-1-non-gdpr-prohibition-purpose> a odrl:Constraint ;
    odrl:leftOperand dpv-odrl:Purpose ;
    odrl:operator odrl:neq ;
    odrl:rightOperand dpv:ServiceProvision .
```