---
layout: post
title: Migrating a module to Vox Pupuli
date: 2016-07-01
summary: Complete directions for migrating a module to Vox Pupuli, including the process for forking and assuming ownership of an abandoned module.
---

You will have someone by your side in this process. The general flow is to…

* Ask one of the Administrators to add you to the `incoming-migrations` team.
* At that point you can transfer your own repository.
* Ensure github issues are enabled.
* Verify that all webhooks are disabled.
* If this module was created with PDK delete .sync.yaml.
* Add the module to our [modulesync setup][managed_modules].
* Enable `Automatically delete head branches` in the repository settings.
* Ask an admin to add the `collaborators` team to the module's `Collaborators & Teams` 'Teams' list with `Write` permissions (e.g. [https://github.com/voxpupuli/puppet-gitlab/settings/collaboration](https://github.com/voxpupuli/puppet-gitlab/settings/collaboration) (that link works only for admins).
* The admin shall also update the [access permissions](https://github.com/organizations/voxpupuli/settings/secrets/actions) (that link works only for admins) for forge.puppet.com secrets so releases can be published.
* Execute [modulesync][msync] for this module.
* Create a Jira issue at [tickets.puppetlabs.com](https://tickets.puppetlabs.com) in the FORGE project and ask to deprecate the old module (and approve the new one if the old one was approved as well).
* Do you think the module qualifies to be approved? Wait until it is released, then raise a [GitHub Issue][approve] in the Puppetlabs organisation.
* Our modulesync will delete a `CONTRIBUTING.md` in the root directory and place one at `.github/CONTRIBUTING.md`. Please enhance [our existing template][template] if the version in the docroot contains useful parts.
* Ensure that the module has a correct `LICENSE` file in the docroot that matches the mentioned license in the `metadata.json`.
* Write a very short blog post about the migration([example][example]). Write to our [mailinglist](mailto:voxpupuli@groups.io) about the migration/new blogpost.

If you have many modules you wish to migrate, this will be cumbersome.
In this case we will generally create a separate group and give you
administrator access to speed things up.

If you are interested in Vox Pupuli accepting a module *that you do not own*, the process has a few extra steps before beginning the checklist above.
We do ask that you show that reasonable efforts have been made to engage the owner and they are unresponsive.
If the owner has responded and is not interested in migrating their module to VP, it will be evaluated on a case by case basis.
To start the process, document your request and efforts in a brief email to the [mailing list](https://groups.io/g/voxpupuli/).
If the module is accepted, VP will work with you to determine the proper fork/migration steps needed in addition to the checklist above.

[managed_modules]: https://github.com/voxpupuli/modulesync_config/blob/master/managed_modules.yml
[msync]: https://github.com/voxpupuli/modulesync_config#modulesync-configs
[template]: https://github.com/voxpupuli/modulesync_config/blob/master/moduleroot/.github/CONTRIBUTING.md.erb
[modules]: https://tickets.puppetlabs.com/projects/MODULES/issues/
[approve]: https://github.com/puppetlabs/puppet-approved-modules/issues/new?assignees=&labels=&template=puppet-approved-modules.md&title=
[example]: https://github.com/voxpupuli/voxpupuli.github.io/blob/master/_posts/2023-12-05-nsswitch-migration.md
