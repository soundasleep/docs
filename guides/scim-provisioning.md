# SCIM Provisioning

Currently, provisioning is only available for Okta.  If you would like to use provisioning with a different identity provider, please [contact us](mailto:support@rollbar.com) and let us know which system you are using.
{: .info}

Rollbar provides a [SCIM](https://en.wikipedia.org/wiki/System_for_Cross-domain_Identity_Management) API that allows for users and teams to be automatically created and managed from external identity providers (IdPs).  IdP-specific instructions are provided below.

{% comment %}
When provisioning is enabled, certain actions in your IdP will automatically update your Rollbar account:

| Action in IdP: | Result in Rollbar account: |
|----------------|----------------------------|
| Assign group to Rollbar app | Rollbar team created. Group members added to Rollbar team.  _NOT|
| Assign user to Rollbar app | **Not recommended:**  Rollbar user create, but they may not be assigned to any teams. |
| Remove group from rollbar app | Rollbar team deleted. |
| Remove user from group assigned to Rollbar app | User removed from  Rollbar team. |

Additionally, any action on a user or group that would cause it to lose access to the Rollbar app (i.e. delete, suspend, deactivate, etc.) will result in the corresponding Rollbar teams/user being removed from the Rollbar account.
{% endcomment %}
## Okta Instructions

NOTE: We recommend you only assign **groups** to the Rollbar application.  Users who are assigned directly (i.e. not as part of a group) to the Rollbar application will be created but may not be assigned to any teams in your account, and may not be able to access any Rollbar projects.
{: .warning}

**In Rollbar:**

* Make sure that you have successfully [configured Okta as your identity provider](../saml/#okta).
* Turn on the **Enable user and team provisioning** option.
* Copy the provided access token.

**In Okta:**

* Make sure that the Rollbar application is added to your your Okta account.
* Click on Rollbar in your application list, then go to the **Provisioning** tab.
* Select **API Integration**, then choose to edit and make sure that **Enable API Integration** is turned on.  Enter the following for the remaining fields:
  * **Base URL**: `https://rollbar.com/ACCOUNT_NAME/scim/v2/okta/`, where `ACCOUNT_NAME` is the name of the Rollbar account you are configuring.
  * **API Token**: The access token you copied from your Rollbar account.
* Click **Test API Credentials** to confirm the configuration and then save it.
* _For each Okta group that you'd like to assign to the Rollbar app:_
  * Go to the **Assignments** tab in the Rolbar application, click **Assign to Groups** and then select the group(s). 
  * Go to the **Push Groups** tab in the Rollbar application, click **Add Group by Name**, enter the name of the group, turn on **Push group memberships immediately**, and choose to **Create Group** if no match is found.

NOTE: You must add groups in _both_ the **Assignments** and **Push Groups** tabs in order for teams and users to be correctly provisioned. 
{: .warning}

**In Rollbar:**

* Confirm that a team has been created for each identity provider group, and that all group members are also team members.
