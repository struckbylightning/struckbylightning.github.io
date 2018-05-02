---
layout: post
published: true
mathjax: false
featured: false
comments: false
title: Define Rollup Fields for Lookup Relationships in Custom Metadata
---
## Declarative Metadata base Rollup Summaries

This code leverages an excellent open source library by [Abhinav Gupta](https://twitter.com/abhinavguptas) and is a Metadata variant of [Andrew Fawcett\`s](https://twitter.com/andyinthecloud) [DLRS](https://github.com/afawcett/declarative-lookup-rollup-summaries) 

Problem that we are solving,

- 25 rollup summary fields allowed per object on master detail relationships
- Rollup child sobject records part of a lookup relationship. Native rollup summary fields are not available on LOOKUP relationships.
- Deploying the metadata configs with ease without use of data loader.
- Multilevel rollups, child field needs to be rolled up on parent, parent\`s field storing rollup inturn needs to be rolled up onto GrandParent

As always first thing first, here\`s the link to Unmanaged Package - https://login.salesforce.com/packaging/installPackage.apexp?p0=04t7F0000051NoL

Here are the steps to follow after you have installed 

1. Define Rollup Object Mapping
![Rollup Object Mappings.png]({{site.baseurl}}/images/Rollup%20Object%20Mappings.png)

2. Define Rollup Field Mapping
![Rollup Field Mappings.png]({{site.baseurl}}/images/Rollup%20Field%20Mappings.png)

3. Create trigger on the child objects whose field needs to be aggregated using below template code, 
  refer to below sample trigger (replace Account with Sobject\`s api name onto which you are creating trigger)

```javascript
trigger AccountTrigger on Account (after insert, after update, after delete, after undelete) {
    Account[] objects = null;  
    if(Trigger.isInsert){
        objects = Trigger.new;        
    }
    else if(Trigger.isUpdate){
        objects = RollupServices.filterUpdatedRollupFieldRecords(Trigger.new, Trigger.oldMap, 'Account');        
    }    
    else if(Trigger.isDelete){
        objects = Trigger.old;
    }    
    else if(Trigger.isunDelete){
        objects = Trigger.new;
    }
    RollupServices.doRollup(objects, 'Account');
}
```