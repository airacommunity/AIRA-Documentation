# AIRA Enterprise Applications Sign-On

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

## Step 6: Navigate to Application Overview
![6](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/84f4b368-60a7-4d66-b5ca-57509d9e6c85)
* Following the creation of your application, you will be redirected to the new application's overview page.
* To configure Single Sign-On settings, locate and select the "Single Sign-On" option from the left navigation bar.

## Step 7: Choose SAML Sign-On Method
![7](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/f8ad3805-2a55-4052-99f9-883aae15556f)
* Within the Single Sign-On settings, a new page will open.
* Look for and select the "SAML" sign-on method to configure SAML-based authentication for your application.

## Step 8: Configure SAML-Based Sign-On
![8](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/180a53a9-856b-4a1b-9100-d501829e5acc)
* After selecting the SAML Sign-On method, a new page titled "SAML-based Sign-on" will be displayed. This section is dedicated to configuring SAML set-up for your application.

## Step 9: Configure Basic SAML Settings

### Edit Basic SAML Configuration

![9](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/14d627b5-16b8-4d19-af17-d91c651d6133)

* Navigate to the "Basic SAML Configuration" section on the "SAML-based Sign-on" page.
* Click on the three dots, located on the right side of the section.
* Choose the "Edit" option to customise the basic SAML configuration.

### Provide Identifier (Entity ID)

![10](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/4a3a4233-86be-4a1c-8423-dc3a443ebf73)

* In the "Edit Basic SAML Configuration" section, locate the field for "Identifier (Entity ID)."

![1 1](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/3379c219-bfc3-4fc9-91b9-9e017197a6e7)

* Access AIRA by logging in and navigating to the Admin section from the left navigation.

![1 2](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/13286a44-8c14-4205-ac9f-38ae0490ca66)

* Within the Admin section, click on "SAML Configuration" to reveal the Entity ID.

![1 3](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/50640d8d-ee8f-40b9-ab03-e5a25ff5d980)

* Copy the Entity ID from AIRA and paste it into the "Add Identifier" field in the Basic SAML Configuration section.

### Reply URL (Assertion Consumer Service URL)

![11](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/21eca054-62f4-4894-be68-0fcbb91d7924)

* In the "Edit Basic SAML Configuration" section, find the field for "Assertion Consumer Service URL."

![1 1](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/ad9f4792-86da-4b53-9854-57d605221a40)

![1 2](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/bdb7b5f7-efa2-45c4-bd03-60de0a3377d8)

* Login to AIRA, go to the Admin section, and then access the SAML Configuration.

![1 4](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/f5ff01b6-92ba-4985-b5bd-3c23f38eb104)

* Retrieve the Assertion Consumer Service URL from AIRA.
* Copy the URL from AIRA and paste it into the "Add Reply URL" field in the Basic SAML Configuration section.
* Save all the Basic SAML Configuration.

## Step 10: Configure Attributes & Claims

![12](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/55e033c7-7888-47ef-826e-25810893527e)

* After configuring the Basic SAML settings, proceed to the "Attributes & Claims" section in the "SAML-based Sign-on" page.
* Within the "Attributes & Claims" section, click on the three dots located on the right side of the section.
* Select the "Edit" option to customise the attribute and claim settings.

### Configure Unique User Identifier (Name ID)

![13](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/a03fb881-5065-46c4-a012-6b7a4c5fe523)

* Once in the "Edit Attributes & Claims" section, search for "Unique User Identifier (Name ID)."

![13-1](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/a49dda12-33cc-480f-a564-d2904cc4141b)

* Click on the value part of this section to open a new window for configuration.
* In the new window, locate the "Source Attribute" field.

![14](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/23c47649-cfc9-4d89-8734-639661a42364)

* Enter "user.mail" as the source attribute. This ensures that the user's email address is used as the unique identifier.
* Save the changes to apply the configuration.

## Step 11: Configure SAML Certificates

![15](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/59ddde88-1f4e-4151-89f4-d4eda7f6a91d)

* After configuring Attributes & Claims, proceed to the "SAML Certificates" section in the "SAML-based Sign-on" page.
* Within the "SAML Certificates" section, click on the three dots located on the right side.
* Choose the "Edit" option to customise the certificate settings.

### Configure Signing Options

![16](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/51033c03-fecc-4458-8260-7fa724c24788)

* After opening the edit tab, locate the "Signing options” is set to be “Sign SAML Assertion”.
* Verify that the "Signing Algorithm" is set to "SHA 256.".
* Save the section.

## Step 12: Configure Verification Certificates

![17](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/7e3b6d3e-c784-4025-92be-479d8bc025a8)

* Within the "SAML Certificates" section, locate the "Verification Certificates" subsection.
* Click on the three dots on the right side of the "Verification Certificates" section.
* Choose the "Edit" option to customise the verification certificate settings.

![18](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/597e12a5-3f88-4603-b494-6055f60f8401)

* After opening the edit tab, check the option that says "Require Verification Certificates."
* In the same section, locate the "Upload" section or a field related to uploading the server public key.
* Upload the server public key file with a ".cer" extension.
* Save the section.

**Note :** Command to generate private and public keys for SAML:
```
Code
openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:4096 -keyout privateKey.key -out certificate.crt
```

## Step 13 : Open and Copy Public and Private Keys
* Open the generated public key (certificate.cer) and private key (privateKey.key) files using a text editor like Notepad or any other code editor.
* Copy the content of the public key file.
  
![1 1](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/fff29d2d-fdfe-4431-9921-5461b7a1b305)
  
* Open the AIRA platform and navigate to the "Admin" section from the left navigation bar.
  
![1 2](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/73318ce2-6f13-4b55-b50d-d1eeaaedd787)

* Within the Admin section, select "SAML Configuration.

![Screenshot 2024-01-11 183517](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/0f502411-289b-49f0-8bca-1bd28c608efc)

* Locate the field for "Public Key" and paste the content of the copied public key into this field.
* Now, go back to the text editor and copy the content of the private key file.
* Return to the AIRA "SAML Configuration" section.
* Find the field for "Private Key" and paste the content of the copied private key into this field.
* Save the changes to apply the public and private key configuration for SAML authentication in AIRA.

## Step 14: Download Certificate (Base64)

![19](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/2ba273d7-40a4-4bce-b3da-8887df8c59e5)

* Within the "SAML Certificates" section, find the "Download Certificate (Base64)" subsection.
* Click on the relevant option to download the certificate in Base64 format.

![1 1](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/ad8f0947-7e5b-447a-b627-aed24739bd2c)

* Open the AIRA platform and select the "Admin" section from the left navigation bar.

![1 2](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/b14babdd-1c3b-4edc-be20-d7c67a39c346)

* Within the Admin section, locate and select the "SAML Configuration" section.
* In the SAML Configuration section, find the area for uploading certificates.

![1 8](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/77c8e655-cac4-4d35-b3aa-e6e1d1ae52bc)

*  the Base64 certificate that you downloaded.

## Step 15: Retrieve Client ID and Tenant ID

![20](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/3378e25f-0eb4-4ae0-9c7d-b8ef3ebbe418)

* In the AIRA Enterprise environment, navigate to the default directory from the top right corner.

![21](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/1448afce-aae0-47a9-86dc-ea5c63e33745)

* Click on "App Registration" from the left navigation bar.

![22](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/586f3826-5946-44c6-92a2-aca6d3c7fefd)

* Choose the name of the application you generated.

### Copy Client ID and Tenant ID

![23](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/95ce925c-0f31-49b0-b9e9-8c6dcb72c78a)

* From the selected application, copy the "Client ID" and "Tenant ID" from the respective sections.

### Paste IDs in AIRA Platform

![1 1](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/991f9c9a-ce10-47a8-a792-e215af5c6f62)

* Open the AIRA platform, select the "Admin" section from the left navigation bar.

![1 2](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/458d48d0-45b8-40db-8dc9-6fb818dd10cc)

* In the Admin section, choose "SAML Configuration."

![1 5](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/450e24e1-95ff-463f-b582-b64de139dea8)

![1 6](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/be426936-9644-48e1-9f2a-1528ff022b4c)

* Paste the copied "Client ID" and "Tenant ID" in their respective sections.

### Add New Secret Client

![21](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/1448afce-aae0-47a9-86dc-ea5c63e33745)

* Click on "App Registration" from the left navigation bar.

![22](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/586f3826-5946-44c6-92a2-aca6d3c7fefd)

* Choose the name of the application you generated.

![23-1](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/d28571c5-15bd-4534-9932-a8b573bf12b5)

* Click on the "Secrets" button in the App Registration section.

![24](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/2954caf7-b144-46f7-8743-078fe93101dd)

* Click on the "New Client Secret" button.

![25](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/4ada0933-b403-4873-8a51-10a5dfb4e65e)

![26](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/f5a38bae-c0de-4947-a01c-976222a65db7)

* Add a description for the new client secret.
* Click on the "Add" button, and a new ID will be generated.

### Copy Client Secret Value

![26](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/f5a38bae-c0de-4947-a01c-976222a65db7)

* Copy the value of the newly generated client secret ID.

### Paste Client Secret in AIRA Platform

![1 1](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/a6d3552f-60a2-42b9-a0be-8f23fc713d06)

* Open the AIRA platform, select the "Admin" section from the left navigation bar.

![1 2](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/d2c0ca21-5e3b-456f-9b90-f1fb544ff3d3)

* In the Admin section, choose "SAML Configuration."

![1 7](https://github.com/airacommunity/AIRA-Documentation/assets/153823636/fba2722f-003d-4191-8088-5e8fd01c3ffd)

* Paste the copied client secret value in the respective section for client credentials.

***
## Conslusion : 

In summary, the guide outlines a comprehensive process for setting up Single Sign-On (SSO) using SAML for AIRA Enterprise Applications on the Azure portal. Users are guided through creating a new application, configuring SAML settings, managing attributes, and establishing SAML certificates for secure authentication. The emphasis is on accuracy in copying essential information. By following these steps, users can seamlessly integrate AIRA applications into their Azure environment, ensuring a secure and efficient Single Sign-On experience. It's essential to stay updated with platform changes and refer to official documentation for the latest information.
***
***










