# SCIM Provisioning

Rollbar provides a [SCIM](https://en.wikipedia.org/wiki/System_for_Cross-domain_Identity_Management) API that allows for users and teams to be automatically created and managed from external identity providers.  Provider-specific instructions are provided below.

Currently, provisioning is only available for Okta.  If you would like to use provisioning with a different identity provider, please [contact us](mailto:support@rollbar.com) and let us know which system you are using.
{: .info}

## Okta Instructions

In order to automatically provision users in Rollbar, we recommend you only assign groups to the Rollbar application.  Users who are assigned directly (i.e. not as part of a group) to the Rollbar application will be created but will not be automatically assigned to any teams in your account, and thus will not be able to access any Rollbar projects.
{: .warning}

**In Rollbar:**

* Make sure that you have successfully [configured Okta as your identity provider](../saml/#okta).
* Turn on the `Enable user and team provisioining` option.
* Copy the provided access token.

**In Okta:**

* Make sure that the Rollbar application is added to your your Okta account.
* TODO:  Figure out where to stick access token for 
* 
