There are many docs in the ASE official documentation now. I usually find ASE documents a little scattered on the Web and each time I’m on an ASE case, I spend a few minutes looking for the right doc. To avoid this, I was collating the links for my own reference and I thought it might be helpful to you too. I’ve put them scenario wise you don’t have to go through everything every time. I hope this helps!

**Author: Madhura Bharadwaj**

## ASE Basics

Introduction: [https://docs.microsoft.com/en-us/azure/app-service/environment/intro](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fapp-service%2Fenvironment%2Fintro&data=04%7C01%7Cjsanders%40microsoft.com%7Cc9328ff900a24bf7782408d91c9c9b3a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637572281206262089%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=gM%2FwfHsn0vidSOryGDnDgV87auGGjq3GpkCr8x4R880%3D&reserved=0)

Create External ASE: [https://docs.microsoft.com/en-us/azure/app-service/environment/create-external-ase](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fapp-service%2Fenvironment%2Fcreate-external-ase&data=04%7C01%7Cjsanders%40microsoft.com%7Cc9328ff900a24bf7782408d91c9c9b3a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637572281206272081%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=F2boYYgsWnKeFGpxW4CmeekQLG15U0XPpM0R3h96lTI%3D&reserved=0)

Create Internal ASE: [https://docs.microsoft.com/en-us/azure/app-service/environment/create-ilb-ase](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fapp-service%2Fenvironment%2Fcreate-ilb-ase&data=04%7C01%7Cjsanders%40microsoft.com%7Cc9328ff900a24bf7782408d91c9c9b3a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637572281206282079%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=P6TV1NW%2FTRUXIb4Gepeyo7zIurspBI4jdvYC1j4IjLE%3D&reserved=0)

Creating ASE with ARM template: [https://docs.microsoft.com/en-us/azure/app-service/environment/create-from-template](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fapp-service%2Fenvironment%2Fcreate-from-template&data=04%7C01%7Cjsanders%40microsoft.com%7Cc9328ff900a24bf7782408d91c9c9b3a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637572281206292072%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=KYD3m%2BEsFVetpAZ2bR%2B8mmdNxXVSWJnyh%2BWBQ9ebnSo%3D&reserved=0)

Using an ASE: <https://docs.microsoft.com/en-us/azure/app-service/environment/using-an-ase>



## ASE Networking/Routing Concepts

Network Considerations: [https://docs.microsoft.com/en-us/azure/app-service/environment/network-info](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fapp-service%2Fenvironment%2Fnetwork-info&data=04%7C01%7Cjsanders%40microsoft.com%7Cc9328ff900a24bf7782408d91c9c9b3a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637572281206312061%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=%2BcZtT4lV9OigKOlzIHA8m%2FIGAhusqUBDNfkGdtgkoxA%3D&reserved=0)

Controlling inbound traffic: [https://docs.microsoft.com/en-us/azure/app-service/environment/app-service-app-service-environment-control-inbound-traffic](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fapp-service%2Fenvironment%2Fapp-service-app-service-environment-control-inbound-traffic&data=04%7C01%7Cjsanders%40microsoft.com%7Cc9328ff900a24bf7782408d91c9c9b3a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637572281206322055%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=v5WgvR00QcjaheOehEWM1B9jxOwmws42U%2FG0Sz%2FzkNI%3D&reserved=0)

Network Configuration for ASE + ExpressRoute: [https://docs.microsoft.com/en-us/azure/app-service/environment/app-service-app-service-environment-network-configuration-expressroute](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fapp-service%2Fenvironment%2Fapp-service-app-service-environment-network-configuration-expressroute&data=04%7C01%7Cjsanders%40microsoft.com%7Cc9328ff900a24bf7782408d91c9c9b3a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637572281206332057%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=YvId09TvzNMHOfZFrO%2FG5cflPo4C%2BgJ4OgeEf2xzLWg%3D&reserved=0)

Connecting to backend resources from an ASE: <https://docs.microsoft.com/en-us/azure/app-service/environment/app-service-app-service-environment-securely-connecting-to-backend-resources>



## ASE Config

ASE Encryption/TLS: [https://docs.microsoft.com/en-us/azure/app-service/environment/app-service-app-service-environment-custom-settings](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fapp-service%2Fenvironment%2Fapp-service-app-service-environment-custom-settings&data=04%7C01%7Cjsanders%40microsoft.com%7Cc9328ff900a24bf7782408d91c9c9b3a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637572281206352049%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=OgHsjxBWz0YmNlOpVKuBDs4mdvQAtmcr0yWmNGh1N%2Fs%3D&reserved=0)

<u>ASE with other devices(WAF/Firewall/Gateway):</u>

ASE + Firewall (lockdown ASE): [https://docs.microsoft.com/en-us/azure/app-service/environment/firewall-integration](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fapp-service%2Fenvironment%2Ffirewall-integration&data=04%7C01%7Cjsanders%40microsoft.com%7Cc9328ff900a24bf7782408d91c9c9b3a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637572281206362037%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=%2BBnWK%2FRE6GHlAG7sGgfMUiVOYdHxEBCWAcIbvwJYEGE%3D&reserved=0)

ILB ASE + Azure App GW: [https://docs.microsoft.com/en-us/azure/app-service/environment/integrate-with-application-gateway](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fapp-service%2Fenvironment%2Fintegrate-with-application-gateway&data=04%7C01%7Cjsanders%40microsoft.com%7Cc9328ff900a24bf7782408d91c9c9b3a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637572281206372035%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=Yj%2BHe2uBQ6tUvmC45ihfqw6wNrUMdsaBNYz4ir5M2n0%3D&reserved=0)

WAF on App Gateway: [https://docs.microsoft.com/en-us/azure/web-application-firewall/ag/ag-overview](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fweb-application-firewall%2Fag%2Fag-overview&data=04%7C01%7Cjsanders%40microsoft.com%7Cc9328ff900a24bf7782408d91c9c9b3a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637572281206382032%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=ga92uPTjL1nSqsJsllWzmX9%2Bk64KKHFWF70UzAuOQ%2BE%3D&reserved=0)

ASE + Barracuda Firewall: [https://docs.microsoft.com/en-us/azure/app-service/environment/app-service-app-service-environment-web-application-firewall](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fapp-service%2Fenvironment%2Fapp-service-app-service-environment-web-application-firewall&data=04%7C01%7Cjsanders%40microsoft.com%7Cc9328ff900a24bf7782408d91c9c9b3a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637572281206392026%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=6aM%2FbbdfIhzXrkl4%2BN7y4F3XMBfwhtbiDQuBGHJd2m8%3D&reserved=0)

ASE + Network Virtual Appliance (force tunneling): <https://docs.microsoft.com/en-us/azure/app-service/environment/forced-tunnel-support>

## 

## Reference Architectures/Diagrams

App Service Networking Features(when to choose what): [https://docs.microsoft.com/en-us/azure/app-service/networking-features](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fapp-service%2Fnetworking-features&data=04%7C01%7Cjsanders%40microsoft.com%7Cc9328ff900a24bf7782408d91c9c9b3a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637572281206402021%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=po8Ebc8cU7xcCTq3Rg4V6Q0vD4wsoa42YaY6z4cfLkE%3D&reserved=0)

ASE Enterprise App Deployment: [https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/enterprise-integration/ase-standard-deployment](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Farchitecture%2Freference-architectures%2Fenterprise-integration%2Fase-standard-deployment&data=04%7C01%7Cjsanders%40microsoft.com%7Cc9328ff900a24bf7782408d91c9c9b3a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637572281206412022%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=vXoXywGTWRwhL2BooR9OD9Vu3%2B%2BHcdZg3zR65jqyRps%3D&reserved=0)

ASE High availability deployment: [https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/enterprise-integration/ase-high-availability-deployment](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Farchitecture%2Freference-architectures%2Fenterprise-integration%2Fase-high-availability-deployment&data=04%7C01%7Cjsanders%40microsoft.com%7Cc9328ff900a24bf7782408d91c9c9b3a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637572281206422009%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=aXNONUmW5uWmzKya%2Fi7Jb0tJuk%2BXYLm90n3oR%2F%2FTcH4%3D&reserved=0)

Geo Distributed scale with ASE: <https://docs.microsoft.com/en-us/azure/app-service/environment/app-service-app-service-environment-geo-distributed-scale>



## Other related info

Network Security Groups (NSGs): [https://docs.microsoft.com/en-us/azure/virtual-network/security-overview](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fvirtual-network%2Fsecurity-overview&data=04%7C01%7Cjsanders%40microsoft.com%7Cc9328ff900a24bf7782408d91c9c9b3a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637572281206442006%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=iKaT87yZ1hgnkds2J8ePL%2FwjZ%2B3BoxSJBXtocihHl1M%3D&reserved=0)

About UDR, BGP Routes, System Routes: [https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-udr-overview](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fvirtual-network%2Fvirtual-networks-udr-overview&data=04%7C01%7Cjsanders%40microsoft.com%7Cc9328ff900a24bf7782408d91c9c9b3a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637572281206452005%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=ITatoNAhiLlGHXiyLDwneHJpEIyTTK8vAJAbTqTosOQ%3D&reserved=0)

Azure Firewall & Network Virtual Appliance (NVA): [https://azure.microsoft.com/en-us/blog/azure-firewall-and-network-virtual-appliances/](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fazure.microsoft.com%2Fen-us%2Fblog%2Fazure-firewall-and-network-virtual-appliances%2F&data=04%7C01%7Cjsanders%40microsoft.com%7Cc9328ff900a24bf7782408d91c9c9b3a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637572281206461996%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=%2B%2FFx0bXpNT%2Fa691lNnDzw00DZtBt3z1d5j9euorQlOU%3D&reserved=0)

Availability Zone Support for ASE: [https://docs.microsoft.com/en-us/azure/app-service/environment/zone-redundancy](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fapp-service%2Fenvironment%2Fzone-redundancy&data=04%7C01%7Cjsanders%40microsoft.com%7Cc9328ff900a24bf7782408d91c9c9b3a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637572281206461996%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=zOlWGRkERzdeUwANfHULiPN5UVsBNQqQ0YHFHJG5UzA%3D&reserved=0)