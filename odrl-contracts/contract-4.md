# Contract 3 - Usage allowed for service provision and service improvement analytics + receive a copy of service data

## User Policy -- GDPR variant

```ttl
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX odrl: <http://www.w3.org/ns/odrl/2/>
PREFIX dpv-odrl: <https://w3id.org/dpv/mappings/odrl#>
PREFIX dpv: <https://w3id.org/dpv#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

<http://example.org/contract-4-gdpr> a odrl:Offer ;
    odrl:uid <http://example.org/contract-4-gdpr> ;
    odrl:profile <https://w3id.org/dpv/mappings/odrl> ;
    dcterms:description "Usage allowed for service provision and service improvement analytics, and the user receives a copy of service data.";
    odrl:conflict odrl:perm ;
    odrl:permission <http://example.org/contract-4-gdpr-permission> ;
    odrl:prohibition <http://example.org/contract-4-gdpr-prohibition> ;
    odrl:obligation <http://example.org/contract-4-gdpr-obligation> .

<http://example.org/contract-4-gdpr-permission> a odrl:Permission ;
    odrl:action odrl:use ;
    odrl:target <http://example.org/alice-data> ;
    odrl:assigner <http://example.org/alice> ;
    odrl:constraint <http://example.org/contract-4-gdpr-permission-purpose> .

<http://example.org/contract-4-gdpr-permission-purpose> a odrl:Constraint ;
    odrl:leftOperand dpv-odrl:Purpose ;
    odrl:operator odrl:isAnyOf ;
    odrl:rightOperand dpv:ServiceProvision, dpv:ServiceOptimisation, dpv:ServiceUsageAnalytics .

<http://example.org/contract-4-gdpr-prohibition> a odrl:Prohibition ;
    odrl:action dpv-odrl:Profiling ; # tracking is missing
    odrl:target <http://example.org/alice-data> ;
    odrl:assigner <http://example.org/alice> .

<http://example.org/contract-4-gdpr-obligation> a odrl:Duty ;
    odrl:action dpv-odrl:Share ;
    odrl:target <http://example.org/service-data> ;
    odrl:assigner <http://example.org/alice> .

<http://example.org/service-data> a dpv:ServiceData .
```