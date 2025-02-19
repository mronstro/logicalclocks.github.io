# Managed.hopsworks.ai Single Sign-On
We will see here how to set up Single Sign-On for [managed.hopsworks.ai](https://managed.hopsworks.ai). Once this is set up users from your organization will be able to directly sign in to [managed.hopsworks.ai](https://managed.hopsworks.ai) using your identity provider and without the need to manually create an account.
They will then be able to manage the clusters of your organization and if you set up [user management](../user_management.md) on your clusters an account will automatically be created for them in the clusters.

!!! Note
    See [Hopsworks Single Sing-On](oauth.md) if you do not want to give users the rights to manage your organization clusters but want to use your identity provider to manage access to your Hopsworks clusters.

## Configure your identity provider.
We will give here the examples of Azure Active Directory and AWS Single Sign-On but a similar setup can be done with any identity provider supporting SAML.

### Azure Active Directory
Go to your [managed.hopsworks.ai dashboard](https://managed.hopsworks.ai/dashboard). Click on *Settings*. Click on *SSO*. Click on *Setup SSO*.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/setupsso.png" alt="Setup SSO">
    <figcaption>Setup SSO</figcaption>
  </figure>
</p>

Click on *Azure Active Directory*. You will need the two copyable entries on this page in the following steps.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/azure_active_directory.png" alt="Azure Active Directory">
    <figcaption>Azure Active Directory</figcaption>
  </figure>
</p>

Go to the [Azure Portal](https://portal.azure.com) then proceed to the [Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview) and click on [Enterprise applications](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AllApps/menuId/). Click on *New application*.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/new_app.png" alt="New application">
    <figcaption>New application</figcaption>
  </figure>
</p>

Search for *hopsworks.ai*. Click on it then click on *create*.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/create_new_app.png" alt="Create your own application">
    <figcaption>Create your own application</figcaption>
  </figure>
</p>

Click on *Single sign-on*. Then click on *SAML*.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/saml.png" alt="SAML">
    <figcaption>SAML</figcaption>
  </figure>
</p>

Click on *Edit* in the *Basic SAML Configuration* section. Paste the *Identifier (Entity ID)* and *Reply URL* that you copied from the [managed.hopsworks.ai](https://managed.hopsworks.ai) setup page. 
Delete the wild card *Identifier (Entity ID)* that is already set.

For the *Sign on URL* copy the provided pattern (*https://managed.hopsworks.ai/sso-open/<ORGANIZATION>*) and replace *ORGANIZATION* by the name of your organization.

Click on *Save*.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/configure_saml.png" alt="Configure SAML">
    <figcaption>Configure SAML</figcaption>
  </figure>
</p>

In the *SAML Signing Certificate* section copy the *App Federation Metadata URL*.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/metadata_url.png" alt="App Federation Metadata URL">
    <figcaption>App Federation Metadata URL</figcaption>
  </figure>
</p>

Click on *Users and groups*, in the left column, and add the users and groups you want to have access to [managed.hopsworks.ai](https://managed.hopsworks.ai).

Go back to [managed.hopsworks.ai](https://managed.hopsworks.ai). Click on *Next step* and keep following the documentation at [Configure managed.hopsworks.ai](#configure-hopsworksai).

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/next_step_azure.png" alt="Next step">
    <figcaption>Next step</figcaption>
  </figure>
</p>

Set the organization name you chose above. This name will be used in your login URL so choose something you will remember. Here we will use *hopsworks-demo*.

Paste the *Metadata URL* you copied above and click *Finish*.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/hopsworks_config.png" alt="Configure managed.hopsworks.ai">
    <figcaption>Configure managed.hopsworks.ai</figcaption>
  </figure>
</p>

!!!Note
    if the organization name you chose is already used you will need to set a new one and to update the *Sign on URL* in Azure.

If you go back to the *SSO* tab of *Settings* you will get a *logging page* link. By using this link you will automatically be redirected to your identity provider to login. An account will automatically be created in [managed.hopsworks.ai](https://managed.hopsworks.ai) for users of your organization when they log in for the first time.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/login_url.png" alt="Configure managed.hopsworks.ai">
    <figcaption>Configure managed.hopsworks.ai</figcaption>
  </figure>
</p>

### AWS Single Sign-On
Go to your [managed.hopsworks.ai dashboard](https://managed.hopsworks.ai/dashboard). Click on *Settings*. Click on *SSO*. Click on *Setup SSO*.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/setupsso.png" alt="Setup SSO">
    <figcaption>Setup SSO</figcaption>
  </figure>
</p>

Click on *AWS SSO*. You will need the copyable entries on this page in the following steps.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/aws_sso.png" alt="AWS SSO">
    <figcaption>AWS SSO</figcaption>
  </figure>
</p>

Go to [AWS Single Sign-On](https://console.aws.amazon.com/singlesignon) in the AWS Management Console and click on *Applications*, then click on *Add New Application*.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/aws_add_app.png" alt="Add New application">
    <figcaption>Add New application</figcaption>
  </figure>
</p>

Click on *Add a custom SAML 2.0 application*.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/aws_add_custom_app.png" alt="Add a custom SAML 2.0 application">
    <figcaption>Add a custom SAML 2.0 application</figcaption>
  </figure>
</p>

Give a name to your application, for example, *hopsworks_sso*. Scroll to the bottom and click on *If you don't have a metadata file, you can manually type your metadata values*.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/aws_app_config.png" alt="Application configuration">
    <figcaption>Application configuration</figcaption>
  </figure>
</p>

Paste the *Application ACS URL* and *Application SAML audience* that you copy from the [managed.hopsworks.ai](https://managed.hopsworks.ai) setup page. Click on *Save changes*.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/aws_app_config2.png" alt="Application configuration 2">
    <figcaption>Application configuration 2</figcaption>
  </figure>
</p>

Go to the *Attribute mappings* tab. On the first line enter the value *Subject* and select *unspecified* for the format. then, Click on *Add new attribute mapping* 3 times.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/aws_attribute_mapping.png" alt="Attribute mapping">
    <figcaption>Attribute mapping</figcaption>
  </figure>
</p>

For each of the created lines enter the following values in the first and second columns and let the format as unspecified.

 * First: *http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress*, second: *${user:email}*
 * First: *http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname*, Second: *${user:familyName}*
 * First: *http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname*, Second: *${user:givenName}*

Click on *Save changes*.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/aws_attribute_mapping2.png" alt="Attribute mapping 2">
    <figcaption>Attribute mapping 2</figcaption>
  </figure>
</p>

Return to the *Configuration* tab and click on *Edit configuration*.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/aws_edit_conf.png" alt="Edit configuration">
    <figcaption>Edit configuration</figcaption>
  </figure>
</p>

Click on Copy URL on the *AWS SSO SAML metadata file* line. We will call this URL *Metadata URL* in the coming steps.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/aws_metadata_url.png" alt="Metadata URL">
    <figcaption>Metadata URL</figcaption>
  </figure>
</p>

Go back to [managed.hopsworks.ai](https://managed.hopsworks.ai). Click on *Next step*.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/next_step_azure.png" alt="Next step">
    <figcaption>Next step</figcaption>
  </figure>
</p>

Give a name to your organization. This name will be used in your login URL so choose something you will remember. Here we will use *hopsworks-demo*.

Paste the *Metadata URL* you copied above and click *Finish*.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/hopsworks_config.png" alt="Configure managed.hopsworks.ai">
    <figcaption>Configure managed.hopsworks.ai</figcaption>
  </figure>
</p>

If you go back to the *SSO* tab of *Settings* you will get a *logging page* link. By using this link you will automatically be redirected to your identity provider to login. An account will automatically be created in [managed.hopsworks.ai](https://managed.hopsworks.ai) for users of your organization when they log in for the first time.

<p align="center">
  <figure>
    <img style="border: 1px solid #000" src="../../../../assets/images/setup_installation/managed/common/sso/login_url.png" alt="Configure managed.hopsworks.ai">
    <figcaption>Configure managed.hopsworks.ai</figcaption>
  </figure>
</p>
