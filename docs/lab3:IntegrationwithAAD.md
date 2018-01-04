## Lab 02: Deploying OpenShift cluster using ARM templates

* [Exercise 01: Create an Azure AD Application](#exercise-01-create-an-azure-ad-application)
* [Exercise 02: Create a KeyVault](#exercise-02-create-a-keyvault)
* [Exercise 03: Deploy OpenShift Cluster using ARM Template](#exercise-03-deploy-openshift-cluster-using-arm-template)
* [Exercise 04: Configure Azure AD Authentication](#exercise-04-configure-azure-ad-authentication)
   
 
### Lab Overview
In this lab, you will learn how to **deploy the OpenShift Cluster** on **Azure** using ARM templates.
### Prerequisites
*	Lab 01 must be completed

### Time Estimate
120 minutes

### Exercise 01: Create an Azure AD Application
In this exercise, you will create an Azure AD App and retrieve the Client ID and Client secret values.
1.	**Launch** a browser and **Navigate** to https://portal.azure.com. **Login** with the Microsoft Azure credentials you received via email.
<img src="../images/6azure_dashboard.jpg"/>


2.	**Click** on the **Azure Active Directory** button in the **Menu navigation** bar to view the **Azure Active Directory** blade.
<img src="../images/14selectazure_ad.jpg"/>

3.	You will be directed to the Azure Active Directory blade, **click** on **App registrations**.
<img src="../images/15app_reg.jpg"/>

4.	In the next blade, **click** on **New Application Registration** on top of the blade.
<img src="../images/16new_appreg.jpg"/>

5.	In the **Create** blade, **configure** as follows:

-	Name: **(Provide a unique value)**
-	Application type: **Web app/API**
-	Sign-on URL: https://contoso.com

```
Note: We will change this value later during the lab.
```

And then **click** on **Create**.

<img src="../images/17createapp.jpg"/>

6.	You will be redirected to the **App registrations** blade. You can check the app has been created by typing the App Name in the search field.
<img src="../images/18check_app.jpg"/>

If the app has been created, you can see it in the results as shown above.

7.	Click on the **app** you **created** and you will be directed to the App blade.

8.	Copy the **Application Id** and **save** it in a notepad or any text editor for later use.
<img src="../images/19app_id.jpg"/>

9.	Now, **Click** on **Keys** in the settings blade.
<img src="../images/20app_key.jpg"/>

10.	In the **Keys** blade, **configure** as follows:

- Description: **key1**
- Expires: **Never expires**

And **Click** on **Save.**

<img src="../images/21save_key.jpg"/>

11.	After you click on save, the **key value** will be displayed which is the Client Secret.
**Copy** the value into the text editor where you saved the value of **Application Id** for later use.
<img src="../images/22copy_key.jpg"/>

12.   Now go back to the setting blade of the App and Click on **Required permissions.
<img src="../images/53req_permission.jpg"/>

13.   Click on **Grant Permissions** in the blade that come up and then **Click** on **Yes**
<img src="../images/54grant_permission.jpg"/>
<img src="../images/55grantpermission_yes.jpg"/>

## Exercise 04: Configure Azure AD Authentication
In this exercise, you will configure the **AD App** you created for Authentication into the OpenShift console.
1.	**Launch** a browser and **Navigate** to https://portal.azure.com. **Login** with the Microsoft Azure credentials you received via email.
<img src="../images/43az_dashboard.jpg"/>

2.	**Click** on the **Azure Active Directory** button in the **Menu navigation** bar to view the **Azure Active Directory** blade.
<img src="../images/44az_ad.jpg"/>

3.	You will be directed to the Azure Active Directory blade, **click** on **App registrations**.
<img src="../images/45app_reg.jpg"/>

4.	You will be redirected to the **App registrations** blade. You can search the App by typing the name of the App you created earlier, in the search field.
<img src="../images/46select_app.jpg"/>

5.	**Click** on the **app** you created and you will be directed to the App blade.
<img src="../images/47app_blade.jpg"/>

6.	Now Click on **Properties** under Settings blade.
<img src="../images/48app_properties.jpg"/>

7.	In the **Properties** blade, **edit** as follows:
-	App ID URI: (Provide the OpenShift Console URI)
-	Home Page URL type: (Provide the OpenShift Console URI)
And then **click** on **Save**.
<img src="../images/49save_properties.jpg"/>

8.	Once you save the **properties**, close the properties blade.
<img src="../images/50close_properties.jpg"/>

9.	Then you will be **redirected** to the Settings Blade of **AD App**. Click on the **Reply URLs**.
<img src="../images/51reply_url.jpg"/>

10.	Now **modify** the OpenShift console **url** by removing the ‘console’ from the end and appending **‘oauth2callback/AzureAD’** to the url and provide it in the Reply URL blade that come up and then Click on Save. 
<img src="../images/52replyurl_save.jpg"/>

11.	Now to verify that the user is able to **authenticate** to OpenShift console via Azure AD, **Open** a new tab in the browser and **paste** the **OpenShift Console URL** which you copied earlier.
```
Note: Skip the certificate warning
```
<img src="../images/67openshift_console.jpg"/>

12.	Now click on **AzureAD**, you will be redirected to the **Login Page**. Provide the Azure credentials you received via email over there and click on **Sign in**.
<img src="../images/68sign_in.jpg"/>

13.	Once the login is **successful**, you will be redirected to the **OpenShift console**.
<img src="../images/69openshift_cp.jpg"/>  

[<Previous](/docs/Lab%2001:%20Introduction-to-Azure-Portal.md) /
[Next>](/docs/Lab%2003:%20Deploying-workload-on-Openshift.md)
