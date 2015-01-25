# Step-by-step instructions

To obtain a certificate, you need to apply for one at a Certification Authority (CA).
There are many CAs to choose from, but the most convenient one for people in research & higher education in Europe is TERENA's Certificate Service (TCS).

https://tcs-personal-portal.terena.org/

![portal](step1/firefox/tcs-personal-portal.png "portal")"

## 1. Install a certificate using your browser.

You can automatically install a certificate using your browser by logging in to your home organisation (e.g. your university). Click "Login" and select the organisation where you want to authenticate. After succesful login, you will be redirected back to the portal. Attributes like your name and your email address will be disclosed to the TCS service so it knows what data to put in the certificate.

![home](step1/firefox/tcs-personal-portal-home.png "home")

Your browser will be instructed to generate a new key pair. The private key will be stored on your computer, the public key will be sent to the CA, together with your name and email address, and combined in a certificate. The certificate will be available for download shortly after.

Use the following steps. Click "My Certificates":

![new](step1/firefox/tcs-personal-portal-new-certificate.png "new")

Click "New Certificate":

![aup](step1/firefox/tcs-personal-portal-1-aup.png "aup")

Read the information in the linksif you haven't done so already, and click the checkbox if you agree:

![aup-accepted](step1/firefox/tcs-personal-portal-1-aup-accepted.png "aup-accepted")

There are severl ways in which you can generate a key pair. It is easiest to let your browser generate a key pair for you. Click "Next".

![csr](step1/firefox/tcs-personal-portal-3-csr.png "csr")

The data that will appear in your certificate are listed here. Click "Next".

![generate](step1/firefox/tcs-personal-portal-4-generate.png "generate")

Your browser is now generating key material and submits it to the CA for processing: 

![processing](step1/firefox/tcs-personal-portal-4-processing.png "processing")

After a little while, your certificate should be ready:

![install](step1/firefox/tcs-personal-portal-install.png "install")

Click "Install to keystore" to download the certificate and store it into the key store:

![installed](step1/firefox/tcs-personal-portal-installed.png "installed")

You are done! Your certificate is ready for use.

## 2. Export the certificate from your browser to a file

Your certificate can be used from your browser. But to use if for signing email, it must be installed and configured in your mail client. Note that using your certificate with webmail systems like Hotmail or Google mail is not possible. This is because the mail is sent and received on a server instead of on your client. The servers will not have access to your private key for generating signatures or decrypting email.

To Export your certificate from your browser, proceed as follows:


In Firefox, open the list of certificates.

- on windows, go to `Tools` -> `Advanced` -> `Encryption`.
- on OSX, open `Preferences` | `Advanced` | `Certificates`.

Then click `View Certificates` | `Your certificates`.

Your certificate should be listed there. Select the certificate you want to export.

![cm-your-certificates2](thunderbird/cm-your-certificates2.png "cm-your-certificates2")

Click `Backup...` and enter a name to save it to disk.

![cm-your-certificates-export](thunderbird/cm-your-certificates-export.png "cm-your-certificates-export")

If you have set a master password to protect credentials stored in Firefox, enter it so you can read them:

![cm-your-certificates-master-password](thunderbird/cm-your-certificates-master-password.png "cm-your-certificates-master-password")
![cm-your-certificates-master-password-entered](thunderbird/cm-your-certificates-master-password-entered.png "cm-your-certificates-master-password-entered")

You will be asked for a backup password with which your private key is encrypted. 

![cm-your-certificates-create-backup-password](thunderbird/cm-your-certificates-create-backup-password.png "cm-your-certificates-create-backup-password")

Make sure this password is strong enough. Anyone who can access the file and can guess the password gets hold of your private key! The password quality meter will indicate how strong your password is.

![cm-your-certificates-create-backup-password-entered](thunderbird/cm-your-certificates-create-backup-password-entered.png "cm-your-certificates-create-backup-password-entered")

You should now see an alert, stating that your certificate and private key is stored in a backup file:

![cm-your-certificates-create-backup-success](thunderbird/cm-your-certificates-create-backup-success.png "cm-your-certificates-create-backup-success")

You are done. You can exit Firefox, and start your mail client.

## 3. Import the certificate into your mail client

Let's assume you use Thunderbird as your mail client.

![thunderbird-inbox](thunderbird/thunderbird-inbox.png "thunderbird-inbox")

Open the Certificate Manager.

![thunderbird-preferences-advanced](thunderbird/thunderbird-preferences-advanced.png "thunderbird-preferences-advanced")

![tb-cm-your-certificates](thunderbird/tb-cm-your-certificates.png "ThunderBird Certificate Manager-your-certificates")

CLick `Import...` and navigate to the backup file you created in the previous step.

![tb-cm-your-certificates-import](thunderbird/tb-cm-your-certificates-import.png "ThunderBird Certificate Manager your-certificates-import")

Enter the password you used when exporting your certificate.

![tb-cm-your-certificates-backup-password](thunderbird/tb-cm-your-certificates-backup-password.png "ThunderBird Certificate Manager-your-certificates-backup-password")

![tb-cm-your-certificates-backup-password-entered](thunderbird/tb-cm-your-certificates-backup-password-entered.png "ThunderBird Certificate Manager-your-certificates-backup-password-entered")

You should get an alert that your keys and certificate we're imported:

![tb-cm-your-certificates-import-success](thunderbird/tb-cm-your-certificates-import-success.png "ThunderBird Certificate Manager-your-certificates-import-success")

Your certificate whould now be listed under `Your Certificates`:

![tb-cm-your-certificates-installed](thunderbird/tb-cm-your-certificates-installed.png "ThunderBird Certificate Manager-your-certificates-installed")

View:

![tb-cm-your-certificates-installed-general](thunderbird/tb-cm-your-certificates-installed-general.png "ThunderBird Certificate Manager-your-certificates-installed-general")

Details:

![tb-cm-your-certificates-installed-detail](thunderbird/tb-cm-your-certificates-installed-detail.png "ThunderBird Certificate Manager-your-certificates-installed-detail")


## 4. Configure your mail client to use your certificate

Open Account Settings

![tb-account](thunderbird/tb-account.png "ThunderBird account")

Click Security

![tb-account-security](thunderbird/tb-account-security.png "ThunderBird account-security")

Under `Digital Signing`, click `Select...` to open a selection box with your installed certificates

![tb-account-signing-select](thunderbird/tb-account-signing-select.png "ThunderBird account-signing-select")

Select the certificate you want to use with your account. Click "yes" if you want to use the same certificate for encryption.

![tb-account-encrypt](thunderbird/tb-account-encrypt.png "ThunderBird account-encrypt")

You may consider signing your email by default by selecting the checkbox.

![tb-account-security-finished](thunderbird/tb-account-security-finished.png "ThunderBird account-security-finished")

All set! Let's try to sign an email...

## 5. Send yourself a signed e-mail


![tb-sign](thunderbird/tb-sign.png "ThunderBird sign")
![tb-signed](thunderbird/tb-signed.png "ThunderBird signed")
![tb-received](thunderbird/tb-received.png "ThunderBird received")
![tb-verified-large](thunderbird/tb-verified-large.png "ThunderBird verified-large")
![tb-verified](thunderbird/tb-verified.png "ThunderBird verified")
![tb-verified-view](thunderbird/tb-verified-view.png "ThunderBird verified-view")

## 6. Send yourself an encrypted email

![tb-encrypt](thunderbird/tb-encrypt.png "ThunderBird encrypt")
![tb-encrypted](thunderbird/tb-encrypted.png "ThunderBird encrypted")
![tb-encrypted-info](thunderbird/tb-encrypted-info.png "ThunderBird encrypted-info")
![tb-decrypted](thunderbird/tb-decrypted.png "ThunderBird decrypted")
![tb-decrypted-info](thunderbird/tb-decrypted-info.png "ThunderBird decrypted-info")
