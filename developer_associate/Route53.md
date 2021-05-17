## 🗒️ Notes

### Basics

Concepts

- provides 2 services
  1. Register domains
  2. Host zones in managed nameservers
- global service w/single database
- globally resilient

Register Domains

- has relationships w/TLD registries

1. first R53 checks with registry to see if domain is available
2. it creates a zonefile(aka hosted zone) for the domain
3. allocates nameservers for this zone

   ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e1dec041-81ef-4efe-ab43-c76cd5240f3d/Screen_Shot_2021-05-16_at_11.56.01_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e1dec041-81ef-4efe-ab43-c76cd5240f3d/Screen_Shot_2021-05-16_at_11.56.01_PM.png)

Hosted Zones

- create and manage zone files(aka hosted zones) in AWS
- hosted on 4 AWS managed name servers
- can be public
- or private. linked to one/more vpc
- stores records(recordsets)
