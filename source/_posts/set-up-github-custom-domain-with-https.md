---
title: Set up Github Pages custom domain with HTTPS
date: 2017-06-06 00:48:07
tags: ["github", "godaddy", "custom domain", "dns", "https", "cdn"]
---

To set up custom domain with HTTPS on Github Pages, there are 6 steps : 
1. Buy domain 
2. Setup Github Pages CNAME
3. Add domain to Cloudflare
4. Setup Cloudflare A record
5. Change DNS Nameservers
6. Setup HTTPS in Cloudflare
<!-- more -->

## Buy domain 
Buy domain from provider like [Godaddy](https://tw.godaddy.com/), [NameCheap](https://www.namecheap.com/)
## Setup Github Pages CNAME
Go to Repository -> settings -> Custom domain -> Type `YOUR_CUSTOM_DOMAIN` -> Save
{% asset_img "Github_CNAME.png" %}
Github will commit a file called `CNAME` contain `YOUR_CUSTOM_DOMAIN` in repository root like [example](https://github.com/Asing1001/asing1001.github.io/blob/master/CNAME).
{% asset_img "Root_CNAME.png" %}

## Add domain to Cloudflare
Go to [Cloudflare](https://www.cloudflare.com)-> Sign up-> Add Site -> Type `YOUR_CUSTOM_DOMAIN` -> Begin Scan -> Continue Setup
{% asset_img "cloudflare_add_site.png" %}

<!--You could see detail in [Use Cloudflare CDN service](/)-->

## Setup Cloudflare A record
In DNS page, add `A` record which point out by [Github](https://help.github.com/articles/setting-up-an-apex-domain/#configuring-a-records-with-your-dns-provider) :
> 192.30.252.153  
> 192.30.252.154  

{% asset_img "cloudflare_A_record.png" %}

## Change DNS Nameservers
After setup `A` record -> Selct plan -> Continue -> you will be asked to change dns nameservers which suggest by Cloudflare :
{% asset_img "cloudflare_nameservers.png" %}

Now go to your domain provider, and change nameservers which suggest by Cloudflare : 
> mia.ns.cloudflare.com  
> woz.ns.cloudflare.com  

{% asset_img "Godaddy_nameservers.png" "My Godaddy setting for example"%}

## Setup HTTPS in Cloudflare
Go to Page Rules -> Create Page Rule -> type `http://*.{YOUR_CUSTOM_DOMAIN}/*` -> Select `Always Use HTTPS` -> Save and Deploy
{% asset_img "cloudflare_page_rule.png" %}

After few hours, you can start to access your Github Pages by your custom domain with HTTPS, also you got Cloudflare cdn service! Enjoy !

