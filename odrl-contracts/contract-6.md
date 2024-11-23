# Contract 6 - Usage allowed for service provision, service improvement analytics and first party tracking + receive a copy of service data

## User Policy -- GDPR variant

```ttl
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX odrl: <http://www.w3.org/ns/odrl/2/>
PREFIX dpv-odrl: <https://w3id.org/dpv/mappings/odrl#>
PREFIX dpv: <https://w3id.org/dpv#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

<http://example.org/contract-6-gdpr> a odrl:Offer ;
    odrl:uid <http://example.org/contract-6-gdpr> ;
    odrl:profile <https://w3id.org/dpv/mappings/odrl> ;
    dcterms:description "Usage allowed for service provision, service improvement analytics and first party tracking, and the user receives a copy of service data.";
    odrl:conflict odrl:perm ;
    odrl:permission <http://example.org/contract-6-gdpr-permission> ;
    odrl:permission <http://example.org/contract-6-gdpr-1stpartytracking> ; # assumes that FirstPartyTracking is permitted for all purposes
    odrl:prohibition <http://example.org/contract-6-gdpr-prohibition> ;
    odrl:obligation <http://example.org/contract-6-gdpr-obligation> .

<http://example.org/contract-6-gdpr-permission> a odrl:Permission ;
    odrl:action odrl:use ;
    odrl:target <http://example.org/alice-data> ;
    odrl:assigner <http://example.org/alice> ;
    odrl:constraint <http://example.org/contract-6-gdpr-permission-purpose> .

<http://example.org/contract-6-gdpr-permission-purpose> a odrl:Constraint ;
    odrl:leftOperand dpv-odrl:Purpose ;
    odrl:operator odrl:isAnyOf ;
    odrl:rightOperand dpv:ServiceProvision, dpv:ServiceOptimisation, dpv:ServiceUsageAnalytics .

<http://example.org/contract-6-gdpr-1stpartytracking> a odrl:Permission ;
    odrl:action dpv-odrl:FirstPartyTracking ; # FirstPartyTracking missing from DPV
    odrl:target <http://example.org/alice-data> ;
    odrl:assigner <http://example.org/alice> .

<http://example.org/contract-6-gdpr-prohibition> a odrl:Prohibition ;
    odrl:action dpv-odrl:Profiling ;
    odrl:target <http://example.org/alice-data> ;
    odrl:assigner <http://example.org/alice> .

<http://example.org/contract-6-gdpr-obligation> a odrl:Duty ;
    odrl:action dpv-odrl:Share ;
    odrl:target <http://example.org/service-data-including-tracking-data> ;
    odrl:assigner <http://example.org/alice> .

<http://example.org/service-data-including-tracking-data> a dpv:ServiceData, dpv:TrackingData .
```