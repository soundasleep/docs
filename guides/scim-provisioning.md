# SCIM Provisioning

Rollbar provides a [SCIM](https://en.wikipedia.org/wiki/System_for_Cross-domain_Identity_Management) API that allows for users and teams to be automatically created and managed from external identity providers.  Provider-specific instructions are provided below.

When provisioning is enabled, assigning a group in your identity provider to the Rollbar application will result in a team being created in your Rollbar account.  All users who are members of the group will become members of the Rollbar team.  The team can then be assigned to the appropriate Rollbar projects in your account.

If you unassign a group from the Rollbar application in your IdP, the corresponding Rollbar team will be deleted from your account.

If you remove a user from a group in your IdP, they will be removed from the corresponding Rollbar team in your your account.

Currently, provisioning is only available for Okta.  If you would like to use provisioning with a different identity provider, please [contact us](mailto:support@rollbar.com) and let us know which system you are using.
{: .info}

## Okta Instructions

In order to automatically provision users in Rollbar, we recommend you only assign groups to the Rollbar application.  Users who are assigned directly (i.e. not as part of a group) to the Rollbar application will be created but will not be automatically assigned to any teams in your account, and thus will not be able to access any Rollbar projects.
{: .warning}

_**In Rollbar:**_

* Make sure that you have successfully [configured Okta as your identity provider](../saml/#okta).
* Turn on the `Enable user and team provisioining` option.
* Copy the provided access token.

_**In Okta:**_

* Make sure that the Rollbar application is added to your your Okta account.
* TODO:  Figure out where to stick access token for 
* _For each Okta group that you'd like to assign to the Rollbar app:_
  * Go to the **Assignments** tab in the Rolbar application, click **Assign to Groups** and then select the group(s). 
  * Go to the **Push Groups** tab in the Rollbar application, click **Add Group by Name**, enter the name of the group, choose **Push group memberships immediately**, and choose to **Create Group**.

You must add groups in _both_ the **Assignments** and **Push Groups** tabs in order for teams and users to be correctly provisioned. 
{: .warning}

_**In Rollbar:**_

* Confirm that a team has been created for each identity provider group, and that all group members are also team members.
