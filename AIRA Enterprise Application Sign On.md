![5](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/49214a52-4013-4e3c-b1ae-e92375ee551c)# AIRA Enterprise Applications Sign-On

## Step 1 : Login to Your Azure Account
Begin the sign-on process by logging into your Azure account. If you don't have an account, you will need to create one. Ensure that you have the necessary credentials to access the Azure portal.

## Step 2: Access Entra ID from Azure Services
![1](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/2792e0af-1954-42a8-8666-975f1367cc50)

* Once logged in, navigate to the home page of Azure.
* Locate the "Azure Services" section on the home page.
* Select "Entra ID" from the Azure services section. This action will direct you to the Microsoft Entra ID Overview page.

## Step 3: Navigate to Enterprise Application
![2](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/f9bf2344-8c94-4b60-a1e5-908e2e69c9c5)

* In the Microsoft Entra ID Overview page, explore the left navigation bar.
* Scroll down until you find and select "Enterprise Application”. This will lead you to the Enterprise Application section.

## Step 4: Create a New Application
![3](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/38fc1352-5734-4364-821e-8d17dd804607)

* Within the Enterprise Application section, click on the option "New Application" to create a new application.
* After clicking on "New Application", you will be prompted to start creating a new application.

![4](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/6b3fa423-ffec-4965-bc23-2184098be24e)
* Click on the "Create Your Own Application" button to proceed with the application creation process.

## Step 5: Specify Application Name and Create
![5](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/1e11e2ed-4423-4dba-bbc1-e95159d0871b)
* After selecting "Create Your Own Application", a section titled "Create Your Own Application" will be presented.
* Within this section, enter the desired name for your application in the provided field.
* Click on the "Create" button to proceed with the application creation process.

Step 6: Navigate to Application Overview
![6](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/84f4b368-60a7-4d66-b5ca-57509d9e6c85)
* Following the creation of your application, you will be redirected to the new application's overview page.
* To configure Single Sign-On settings, locate and select the "Single Sign-On" option from the left navigation bar.

Step 7: Choose SAML Sign-On Method
![7](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/f8ad3805-2a55-4052-99f9-883aae15556f)
* Within the Single Sign-On settings, a new page will open.
* Look for and select the "SAML" sign-on method to configure SAML-based authentication for your application.

## Step 8: Configure SAML-Based Sign-On
![8](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/180a53a9-856b-4a1b-9100-d501829e5acc)
After selecting the SAML Sign-On method, a new page titled "SAML-based Sign-on" will be displayed. This section is dedicated to configuring SAML set-up for your application.

## Step 9: Configure Basic SAML Settings

### Edit Basic SAML Configuration
![9](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/14d627b5-16b8-4d19-af17-d91c651d6133)
* Navigate to the "Basic SAML Configuration" section on the "SAML-based Sign-on" page.
* Click on the three dots, located on the right side of the section.
* Choose the "Edit" option to customise the basic SAML configuration.

### Provide Identifier (Entity ID)
![10](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/4a3a4233-86be-4a1c-8423-dc3a443ebf73)
In the "Edit Basic SAML Configuration" section, locate the field for "Identifier (Entity ID)."

![1 1](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/3379c219-bfc3-4fc9-91b9-9e017197a6e7)
Access AIRA by logging in and navigating to the Admin section from the left navigation.

![1 2](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/13286a44-8c14-4205-ac9f-38ae0490ca66)
Within the Admin section, click on "SAML Configuration" to reveal the Entity ID.

Copy the Entity ID from AIRA and paste it into the "Add Identifier" field in the Basic SAML Configuration section.
Provide Reply URL (Assertion Consumer Service URL)

In the "Edit Basic SAML Configuration" section, find the field for "Assertion Consumer Service URL."



Login to AIRA, go to the Admin section, and then access the SAML Configuration.

Retrieve the Assertion Consumer Service URL from AIRA.
Copy the URL from AIRA and paste it into the "Add Reply URL" field in the Basic SAML Configuration section.
Save all the Basic SAML Configuration.

