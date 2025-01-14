![Seneca Hubspot-Provider](http://senecajs.org/files/assets/seneca-logo.png)

> _Seneca Hubspot-Provider_ is a plugin for [Seneca](http://senecajs.org)


Provides access to the Hubspot API using the Seneca *provider*
convention. Hubspot API entities are represented as Seneca entities so
that they can be accessed using the Seneca entity API and messages.


[![npm version](https://img.shields.io/npm/v/@seneca/trello-provider.svg)](https://npmjs.com/package/@seneca/trello-provider)
[![build](https://github.com/senecajs/seneca-trello-provider/actions/workflows/build.yml/badge.svg)](https://github.com/senecajs/seneca-trello-provider/actions/workflows/build.yml)
[![Coverage Status](https://coveralls.io/repos/github/senecajs/seneca-trello-provider/badge.svg?branch=main)](https://coveralls.io/github/senecajs/seneca-trello-provider?branch=main)
[![Known Vulnerabilities](https://snyk.io/test/github/senecajs/seneca-trello-provider/badge.svg)](https://snyk.io/test/github/senecajs/seneca-trello-provider)
[![DeepScan grade](https://deepscan.io/api/teams/5016/projects/19462/branches/505954/badge/grade.svg)](https://deepscan.io/dashboard#view=project&tid=5016&pid=19462&bid=505954)
[![Maintainability](https://api.codeclimate.com/v1/badges/f76e83896b731bb5d609/maintainability)](https://codeclimate.com/github/senecajs/seneca-trello-provider/maintainability)


| ![Voxgig](https://www.voxgig.com/res/img/vgt01r.png) | This open source module is sponsored and supported by [Voxgig](https://www.voxgig.com). |
|---|---|


## Quick Example


```js

// Setup - get the key value (<SECRET>) separately from a vault or
// environment variable.
Seneca()
  .use('env', { // the 'env' plugin enables you to use environment variables in your Seneca instance.
    // debug: true,
    file: [__dirname + '/local-env.js;?'], // you can specify the file with your company's data such as id, etc.
    var: {
      $HUBSPOT_ACCESS_TOKEN: '<SECRET>',
    }
  })
  .use('provider', {
    provider: {
      hubspot: {
        keys: {
          accessToken: {
            value: '$HUBSPOT_ACCESS_TOKEN'
          },
        }
      }
    }
  })
  .use('hubspot-provider')

let companyId = await seneca.entity('provider/hubspot/company')
  .load$('id')
  // .load({id: 'id', fields$: ['state', 'city', 'description']}); // you can use fields$_directive to specify the properties you want to get from a company

Console.log('COMPANY DATA', companyId)

companyId.properties.description = 'New description'
companyId = await companyId.save$()

Console.log('UPDATED DATA', companyId)

```

## Install

```sh
$ npm install @seneca/hubspot-provider
```



<!--START:options-->


## Options

*None.*


<!--END:options-->

<!--START:action-list-->


## Action Patterns

* ["role":"entity","base":"hubspot","cmd":"list","name":"company","zone":"provider"](#-roleentitybasehubspotcmdlistnamecompanyzoneprovider-)
* ["role":"entity","base":"hubspot","cmd":"load","name":"company","zone":"provider"](#-roleentitybasehubspotcmdloadnamecompanyzoneprovider-)
* ["role":"entity","base":"hubspot","cmd":"save","name":"company","zone":"provider"](#-roleentitybasehubspotcmdsavenamecompanyzoneprovider-)
* ["sys":"provider","get":"info","provider":"hubspot"](#-sysprovidergetinfoproviderhubspot-)


<!--END:action-list-->

<!--START:action-desc-->


## Action Descriptions

### &laquo; `"role":"entity","base":"hubspot","cmd":"list","name":"company","zone":"provider"` &raquo;

List Hubspot data into an entity.



----------
### &laquo; `"role":"entity","base":"hubspot","cmd":"load","name":"company","zone":"provider"` &raquo;

Load Hubspot data into an entity.



----------
### &laquo; `"role":"entity","base":"hubspot","cmd":"save","name":"company","zone":"provider"` &raquo;

Update/Save Hubspot data into an entity



----------
### &laquo; `"sys":"provider","get":"info","provider":"hubspot"` &raquo;

Get information about the provider.



----------


<!--END:action-desc-->
