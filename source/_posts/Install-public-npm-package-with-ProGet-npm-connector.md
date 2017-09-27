---
title: Install public npm package with ProGet npm connector
date: 2017-09-27 16:31:56
tags: ["ProGet", "npm", "CI", "Jenkins"]
---

For security reason, private CI server may not have internet access. Instead, it connect to private registry like ProGet. To install public npm package, ProGet connector is here to help, steps as following :

1. Go to Connectors => create connectors => Feed type:npm => Save
1. Go to feeds => Create New Feed => Feed type:npm => Feed name:npm
1. Feed Connectors => add connector => registry.npmjs.org
1. Set up npm via command line in server
   `npm config set registry http://{progethost}/npm/npm`

Now try `npm install`, it should work as it connect to public npm registry.

Reference : http://inedo.com/support/documentation/proget/feed-types/npm