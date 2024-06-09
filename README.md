<!-- TODO -->

https://developer.salesforce.com/docs/atlas.en-us.communities_dev.meta/communities_dev/networks_migrating_from_sandbox.htm

https://developer.salesforce.com/docs/atlas.en-us.sfdx_dev.meta/sfdx_dev/sfdx_dev_scratch_orgs_def_file_config_values.htm#so_communities

https://developer.salesforce.com/docs/atlas.en-us.api_meta.meta/api_meta/meta_communitiessettings.htm

Why isn't the configuration file in Hutte being taken from config/project-scratch-def.json?
At the moment, we need to set it up manually. (Screenshot).

When using a sandbox or scratch org that is not having the current config/project-scratch-def.json, https://help.salesforce.com/s/articleView?id=sf.networks_enable.htm&language=en_US&type=5

## Intro

TODO

Behind the scenes, Help Center template is using Aura framework (screenshot), therefore the same guidelines provided in this recipe apply for any other site using Aura framework. (site-types screenshot).

This recipe includes the [cicd-incremental-deployment](https://github.com/hutte-recipes/cicd-incremental-deployment) recipe in order to validate (in a pull request) and deploy the Experience Cloud sites, see more about this recipe in the linked repository.

## Pre-requisites

- Create Help Center Site (Digital Experiences), see screenshots, customize it with a background image, publish it.
- Add the SFDX_AUTH_URL_TARGET_ORG env url (https://github.com/hutte-recipes/cicd-incremental-deployment)

## Commiting / others

Make sure of enabling "Digital Experiences" in "Setup" -> "Feature Settings" -> "Digital Experiences" -> "Settings" (screenshot taken).

For Aura Communities, including Help Center community, where we commit the SiteDotCom instead of the ExperienceBundle (see [Tips and Considerations](https://help.salesforce.com/s/articleView?id=sf.networks_migrating_from_sandbox.htm&type=5)), make sure to:

- replace the `siteAdmin` with a username that exist in the destination org.
- add CommunitiesLanding ApexPage and Apex Controller (with the respective test class), this will make the deployment work (see screenshot 21.16.22).

Apex classes such as `SiteLoginController`, `MyProfilePageController`, Visualforce components such as `SitePoweredBy` or Visualforce such as `SiteLogin` or `CommunitiesTemplate` are automatically created on the destination org when the deployment of the mandatory metadata is successful.

After this deployment of mandatory metadata, we proceed to deploy specific metadata changes that we have done in our site, such as the addition of a background image `Sample`. For this latest, we will deploy the `ContentAsset/sample` metadata, which is the file we originally inserted as background when customizing the site. Note that we don't need to include any other metadata in the commit, this is because this asset file is reference in the SiteDotCome (.site) file, even though it's a binary file and is not human readable.
Also note that this is a recipe providing guidelines and each scenario will have different needs.

References

- https://help.salesforce.com/s/articleView?id=sf.networks_migrating_from_sandbox.htm&type=5
- https://salesforce.stackexchange.com/questions/380032/trails-project-didnt-work-the-deployment
- https://github.com/trailheadapps/ebikes-lwc
