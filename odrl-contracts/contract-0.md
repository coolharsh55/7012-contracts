# Contract 0 - Nothing is allowed

## Assumptions
- Nothing is allowed, unless the individual issuing the policy adds a permissive action to the policy - this is reflected in the chosen conflict resolution strategy, i.e., [odrl:perm](https://www.w3.org/ns/odrl/2/perm).
- Assumes that the data in question is accessible at an IRI, e.g., `http://example.org/alice-data`.
- Assumes that the individual issuing the policy is identifiable through an IRI, e.g., `http://example.org/alice`.
- **[TO DISCUSS]** Current action being restricted is `odrl:use` - we could also use `dpv:Processing` instead to cover more ground.

## User Policy

```ttl
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX odrl: <http://www.w3.org/ns/odrl/2/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

<http://example.org/contract-0> a odrl:Offer ;
    odrl:uid <http://example.org/contract-0> ;
    dcterms:description "Use of data is prohibited.";
    odrl:conflict odrl:perm ;
    odrl:prohibition <http://example.org/contract-0-prohibition> .

<http://example.org/contract-0-prohibition> a odrl:Prohibition ;
    odrl:action odrl:use ;
    odrl:target <http://example.org/alice-data> ;
    odrl:assigner <http://example.org/alice> .
```