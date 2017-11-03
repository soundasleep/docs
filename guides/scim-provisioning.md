# SCIM Provisioning

Rollbar provides a [SCIM](https://en.wikipedia.org/wiki/System_for_Cross-domain_Identity_Management) API that allows for users and teams to be automatically created and managed from external identity providers (IdPs).  IdP-specific instructions are provided below.

When provisioning is enabled, certain actions in your IdP will automatically update your Rollbar account:

| Action in IdP: | Result in Rollbar account: |
|----------------|----------------------------|
| _Assign group to Rollbar app:_ |<ul><li>Rollbar team is created.</li><li>Group members are added as members of the Rollbar team.</li></ul> |
 <!--
   </td>
  </tr>
  <tr>
   <td>
    <em>Assign user to Rollbar app:</em>
   </td>
   <td>
    <em><strong>Not recommended</strong><em>
     <ul><li>Rollbar user is added to account, but not to any teams.</li></ul>
   </td>
  </tr>
  <tr>
   <td>
    <em>Remove group from rollbar app:</em>
   </td>
   <td>
    <ul><li>Rollbar team is deleted.</li></ul>
   </td>
  </tr>
  <tr>
   <td>
    <em>Remove user from group assigned to Rollbar app:</em>
   </td>
   <td>
    <ul><li>User is removed from the Rollbar team.</li></ul>
   </td>
  </tr>
 </tbody>
</table>
-->

Additionally, any action on a user or group that would cause it to lose access to the Rollbar app (i.e. delete, suspend, deactivate, etc.) will result in the corresponding Rollbar teams/user being removed from the Rollbar account.

Currently, provisioning is only available for Okta.  If you would like to use provisioning with a different identity provider, please [contact us](mailto:support@rollbar.com) and let us know which system you are using.
{: .info}

## Okta Instructions

In order to automatically provision users in Rollbar, we recommend you only assign groups to the Rollbar application.  Users who are assigned directly (i.e. not as part of a group) to the Rollbar application will be created but will not be automatically assigned to any teams in your account, and thus will not be able to access any Rollbar projects.
{: .warning}

**In Rollbar:**

* Make sure that you have successfully [configured Okta as your identity provider](../saml/#okta).
* Turn on the **Enable user and team provisioning** option.
* Copy the provided access token.

**In Okta:**

* Make sure that the Rollbar application is added to your your Okta account.
* TODO:  Figure out where to stick access token for 
* _For each Okta group that you'd like to assign to the Rollbar app:_
  * Go to the **Assignments** tab in the Rolbar application, click **Assign to Groups** and then select the group(s). 
  * Go to the **Push Groups** tab in the Rollbar application, click **Add Group by Name**, enter the name of the group, turn on **Push group memberships immediately**, and choose to **Create Group** if no match is found.

You must add groups in _both_ the **Assignments** and **Push Groups** tabs in order for teams and users to be correctly provisioned. 
{: .warning}

**In Rollbar:**

* Confirm that a team has been created for each identity provider group, and that all group members are also team members.
