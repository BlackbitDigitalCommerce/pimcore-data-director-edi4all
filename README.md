# EDI4All Add-on for Pimcore Data Director

This bundle adds result callback function templates to Data Director's attribute mapping to create EDI4All export feeds. 

As it uses Data Director's export capabilities, your BMEcat exports profit by:

* everything is configurable in Pimcore backend user interface - no creation of PHP files or anything similar necessary
* access any data which is connected to exported products, for example you can easily access assigned categories, price information, manufacturers, product features, images etc.
* full flexibility in setting up a transformation pipeline to change values to the desired format (e.g. some BMEcat-processing applications have restrictions on length of some fields)
* optionally, automatically execute exports whenever a product object gets saved whose data gets exported to:
    * prepare export once the data changes, so that the data does not have to be generated in the moment when the export is requested -> very fast exports because the export document is already available in the moment of request -> you will have an always up-to-date BMEcat export
    * upload exports automatically to a target system to always have up-to-date data there
    * automatically send data the other APIs
* intelligent checks whether anything changed since the last export. If nothing changed, export document gets delivered from cache
* access exports via URL, for example to pull BMEcat export into an external system instead of pushing it

## Installation

This bundle is an add-on bundle for [Pimcore Data Director](https://pimcore.com/en/developers/marketplace/blackbit_digital_commerce/pimcore-data-director_e103850). You can buy this Edi4All add-on bundle in the [Blackbit Shop](https://shop.blackbit.com/pimcore-bmecat-import-export/) or write an email to [info@blackbit.de](mailto:info@blackbit.de).

After you have installed Pimcore Data Director you can proceed with the Edi4All bundle installation.

Please contact us to get access to the bundle's [Bitbucket repository](https://bitbucket.org/blackbitwerbung/pimcore-plugins-data-director-edi4all) or you get the plugin code as a zip file. 
When we permit your account to access our repository, please add the repository to the `composer.json` in your Pimcore root folder (see [Composer manual about repositories](https://getcomposer.org/doc/05-repositories.md#vcs)):
```json
"repositories": [
    {
        "type": "vcs",
        "url": "https://bitbucket.org/blackbitwerbung/pimcore-plugins-data-director-edi4all"
    }
],
```

Alternatively if you received the plugin code as zip file, please upload the zip file to your server (e.g. to the Pimcore root folder) and add the following to your `composer.json`:
```json
"repositories": [
    {
        "type": "artifact",
        "url": "path/to/directory/with/zip-file/"
    }
]
```

Then you should be able to execute `composer require blackbit/data-director-edi4all` (or `composer update blackbit/data-director-edi4all --with-dependencies` for updates if you already have this bundle installed) from CLI.

You can always access the latest version by executing `composer update blackbit/data-director-edi4all` on CLI.

## Setup export

Select `Edi4All XML Export` from the list of templates for the `Result Callback function` in Data Director's attribute mapping.

Then the fields of the EDI4All standard will appear as *virtual* fields in attribute mapping. Those fields can be mapped to your data object class fields (and additionally, transformation functions can be applied if necessary). Afterwards you can access the export either via manual export or via URL (via Data Director's REST API).