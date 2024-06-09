<!-- TODO -->

https://developer.salesforce.com/docs/atlas.en-us.communities_dev.meta/communities_dev/networks_migrating_from_sandbox.htm

https://developer.salesforce.com/docs/atlas.en-us.sfdx_dev.meta/sfdx_dev/sfdx_dev_scratch_orgs_def_file_config_values.htm#so_communities

https://developer.salesforce.com/docs/atlas.en-us.api_meta.meta/api_meta/meta_communitiessettings.htm

Why isn't the configuration file in Hutte being taken from config/project-scratch-def.json?
At the moment, we need to set it up manually. (Screenshot).

When using a sandbox or scratch org that is not having the current config/project-scratch-def.json, https://help.salesforce.com/s/articleView?id=sf.networks_enable.htm&language=en_US&type=5

## Intro

TODO

Behind the scenes, Build your own ... LWR Framework.
Note that it's Enhanced LWR, we cannot see "non-enhanced" in the available sites (Sites screenshot).

This recipe includes the [cicd-incremental-deployment](https://github.com/hutte-recipes/cicd-incremental-deployment) recipe in order to validate (in a pull request) and deploy the Experience Cloud sites, see more about this recipe in the linked repository.

## Pre-requisites

- Create TODO (Digital Experiences), see screenshots, customize it with a background image, publish it.
- Add the SFDX_AUTH_URL_TARGET_ORG env url (https://github.com/hutte-recipes/cicd-incremental-deployment)
- Create a helloWorld.js LWC to insert as example in the LWR site.

## Commiting / others

Commit all required metadata by https://help.salesforce.com/s/articleView?id=sf.networks_migrating_from_sandbox.htm&type=5 table for `Enhanced LWR Site` and also include the LWC `helloWorld`.

Make sure of enabling "Digital Experiences" in "Setup" -> "Feature Settings" -> "Digital Experiences" -> "Settings" (screenshot taken).

Make sure to:

- replace the `siteAdmin` with a username that exist in the destination org.

If you get this error

```
force-app/main/default/digitalExperienceConfigs/build_your_own_lwr_recipe1.digitalExperienceConfig-meta.xml  The value for urlPathPrefix in DigitalExperienceConfig isn't valid. Check the value and try again.
```

Then, https://salesforce.stackexchange.com/questions/373845/deploying-experience-site-fails-due-to-the-value-for-urlpathprefix-in-experienc, go to administration and add a URL, see screenshot, then recommit. Committing the
`digitalExperienceConfig` should be enough, but you can also recommit the initially committed metadata in case of doubt, in case of doing this, untick the commit only selected metadata. (Screenshot).

## Tips

Do it incrementally, validate incrementally with PR validate github action

## References

- https://help.salesforce.com/s/articleView?id=sf.networks_migrating_from_sandbox.htm&type=5
- https://salesforce.stackexchange.com/questions/380032/trails-project-didnt-work-the-deployment
- https://github.com/trailheadapps/ebikes-lwc
