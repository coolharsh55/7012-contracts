# Contract 9 - Usage allowed for service provision, service improvement analytics, first party tracking and profiling + share anonymised data with third party

## User Policy -- GDPR variant

```ttl
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX odrl: <http://www.w3.org/ns/odrl/2/>
PREFIX dpv-odrl: <https://w3id.org/dpv/mappings/odrl#>
PREFIX dpv: <https://w3id.org/dpv#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

<http://example.org/contract-9-gdpr> a odrl:Offer ;
    odrl:uid <http://example.org/contract-9-gdpr> ;
    odrl:profile <https://w3id.org/dpv/mappings/odrl> ;
    dcterms:description "Usage allowed for service provision, service improvement analytics, first party tracking and profiling, and share anonymised data with third party.";
    odrl:conflict odrl:perm ;
    odrl:permission <http://example.org/contract-9-gdpr-permission> ;
    odrl:permission <http://example.org/contract-9-gdpr-tracking-profiling> ; # assumes that FirstPartyTracking, FirstPartyProfiling, ThirdPartyProfiling is permitted for all purposes
    odrl:permission <http://example.org/contract-9-gdpr-share-3rdparty> .

<http://example.org/contract-9-gdpr-permission> a odrl:Permission ;
    odrl:action odrl:use ;
    odrl:target <http://example.org/alice-data> ;
    odrl:assigner <http://example.org/alice> ;
    odrl:constraint <http://example.org/contract-9-gdpr-permission-purpose> .

<http://example.org/contract-9-gdpr-permission-purpose> a odrl:Constraint ;
    odrl:leftOperand dpv-odrl:Purpose ;
    odrl:operator odrl:isAnyOf ;
    odrl:rightOperand dpv:ServiceProvision, dpv:ServiceOptimisation, dpv:ServiceUsageAnalytics .

<http://example.org/contract-9-gdpr-tracking-profiling> a odrl:Permission ;
    odrl:action :FirstPartyTracking, :FirstPartyProfiling, :ThirdPartyProfiling ; # FirstPartyTracking, FirstPartyProfiling, ThirdPartyProfiling missing from DPV
    odrl:target <http://example.org/alice-data> ;
    odrl:assigner <http://example.org/alice> .

<http://example.org/contract-9-gdpr-share-3rdparty> a odrl:Permission ;
    odrl:action dpv-odrl:Share ;
    odrl:target <http://example.org/anonymised-data> ;
    odrl:assigner <http://example.org/alice> ;
    odrl:assignee <http://example.org/third-party> . # is it with just one (or a defined list of) third party or is it valid for any third party? 

<http://example.org/anonymised-data> a dpv:AnonymousServiceData .
```