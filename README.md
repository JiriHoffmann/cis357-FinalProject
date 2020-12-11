# CIS 357 - Final Project

## Submitting apps to Google Play and App Store

This guide will show you all the steps to get your app uploaded to both Google Play and App Store. It is assumed that at this point your app is mostly ready to be distributed to users via the stores. The reason behind this is because adding and removing feature might require you to make changes to your store listings and it's much easier to do it all at once, instead of having to search though the settings and re-doing it.

## Contents

 -  **[Google Play](#google-play)**
    - [Creating a developer account](#creating-developer-account)
    - [Creating the app](#creating-the-app)
    - [App access](#app-access)
    - [Content rating](#content-rating)
    - [Target audience](#target-audience)
    - [News app](#news-app)
    - [Select an app category](#select-app-category)
    - [Store listing](#store-listing)
    - [Publish your app on Google Play](#publish-your-app-on-google-play)
    - [App singing](#app-singing)
    - [Generating a key](#generating-a-key)
    - [Uploading to Google Play](#uploading-to-google-play)
<span> </p>

- **[App Store](#app-store)**
    - [App publishing](#app-publishing)
    - [Version Information](#version-information)
    - [App Clip](#app-clip)
    - [iMessage App](#imessage-app)
    - [Apple Watch](#apple-watch)
    - [Build](#build)
    - [General App Information](#general-app-information)
    - [App Review Information](#app-review-information)
    - [Version Release](#version-release)
    - [Almost ready](#almost-ready)



## ![GP_icon](https://github.com/JiriHoffmann/cis357-FinalProject/blob/main/images/google_play_icon.png?raw=true) Google Play

### Creating developer account

Creating a new developer account is the first and required step to publishing your app on Google Play store. This used to be free, but now Google charges a 25$ registration fee. Start your registration <strong>[here][register-play-console]</strong>.

[register-play-console]: https://play.google.com/console/signup

<p align="center">
  <img src="https://github.com/JiriHoffmann/cis357-FinalProject/blob/main/images/create_account_GPC.png?raw=true" />
</p>

### Creating the app
We will start out by creating the app and adding some basic information about it. While you are able to change any information in here, you should know, that it is possible to change a paid app to free but a **free app cannot be changed to paid**.

<p align="center">
  <img src="https://github.com/JiriHoffmann/cis357-FinalProject/blob/main/images/create_app_GPC.png?raw=true" />
</p>



Now, that we have created the app we are redirected to the dashboard, where we have access to all of the features and settings provided by the Google Play Console. On the dashboard we can see the `Set up your app` tab which is the first required step to be completed before the app can be published.

<p align="center">
  <img src="https://github.com/JiriHoffmann/cis357-FinalProject/blob/main/images/set_up_app_GPC.png?raw=true" />
</p>

### App access

In the first step we have to let Google know if all users can access all of the app’s features or if some of them are limited with a registration or some other form of account creation mechanism. Apps with restricted access require a brief description on how all of it's content can be accessed.



### Content rating

Content rating is a short questionnaire about the content of the app. First developers are asked select one of the provided categories which best describes the functionality of the app. This will be followed by a couple of questions based on the category selected in the previous question and then you can see how the app will be rated in different countries. The questionare can be filled out again at any time in case the content of the app changes.


### Target audience

In Target audience you have to select the target age groups of your app, but before you can do so the Ads section has to be filled out. This is very simple as we just pick if the app will contain ads or not. Choices in both of these categories will affect what your privacy policy must include.


### News app

Just a quick confirmation if the app is a news app or not, due to terms of service for Google News in case it includes news content.


### Selecting app category

This tab focuses on discoverability of the app. We will be adding a category where the app can be found and tags to help improve organic searching as well as some additional contact information in case there are any additional questions during the review.


### Store listing

This will be the most important part for users. Here we set up the app listings, provide descriptions and screenshots for different screen sizes. There are some very specific requirements for image sizes so make sure to take a look at them before creating the images.

<p align="center">
  <img src="https://github.com/JiriHoffmann/cis357-FinalProject/blob/main/images/listing_requirements_GPC.png?raw=true" />
</p>


Once all these steps are done, the app is almost ready to be published. Google also provides great ways to test the app with a limited number of users before it gets officially published so you should definitely check it out.


### Publish your app on Google Play

<p align="center">
  <img src="https://github.com/JiriHoffmann/cis357-FinalProject/blob/main/images/publish_app_GPC.png?raw=true" />
</p>

First off, you will have select countries where the app will be available. Then, we will be returning back to Android Studio to generate a signed apk or Android app bundle. 

Android app bundles are preferred over apk. Bundles allow Google Play to serve individual apks to users based on their device configuration such as processor architecture or assets depending on the screen resolution.


### App singing

The way app signing works on Android is that developers have to generate a ***signing key*** and use it to sign the app. The key has to be consistent across the entire app’s lifetime to ensure all updates are coming from the same developers. This obviously caused many issues if the key was lost as there was no way of recovering it. So Google decided to refactor how signing works. There is now an opt in feature which let’s developers sign the apk with their ***upload key***. The ***upload key*** works the same way as the ***signing key*** but it’s only used to upload the app to Google Play. Google then generates its own ***signing key*** and uses it to re-sign the app and stores it in their database. The added benefit of this approach is that developers can generate a new upload key if lost and the app will remain signed with the same key. I recommend reading more on this topic <strong>[here][app-signing]</strong>.

[app-signing]: https://github.com/facebook/react-native/blob/master/LICENSE-docs

### Generating a key

The easiest way to generate a key is by using Android Studio.

1. In the top bar go to: Build > Generate Signed Bundle/APK
2. Select Android App Bundle or APK and hit next
3. In the Key store path click on Create new…
4. Fill out all required fields and a new key will be generated
5. If your app is ready to build you can continue the walkthrough which will let you generate the app bundle or apk. 
6. The app bundle or apk will be generated in app/build/outputs/release or debug based on the previous selection
7. If you want to verify that the app was signed with the correct key go to your java folder and in jdk/bin run 
`jarsigner -verify -verbose -certs app_name.apk` or use the apksigner provided by Google which can be found under `Android\Sdk\build-tools\`.


### Uploading to Google Play

Now that you have generated a signed app, go back to the Google Play Console website. First, if you would like to let Google generate and store the signing key hit Continue and upload the .aab or .apk file. After that click on Review release. Next up, you can see all the errors and warnings for the current release. For example, my app uses the camera so I have to go back and add a Privacy Policy. If there aren’t any warnings you are all set to hit ***Start rollout to Production***. Be sure your app is ready to be released! This will send the app for a review to Google. Once the review is done you can finally publish the app and let other users download it!




## ![AS_icon](https://github.com/JiriHoffmann/cis357-FinalProject/blob/main/images/app_store_icon.png?raw=true) App Store
 

To be able to share your apps on the App Store, each user has to join Apple Developer Program first. In order to do so, you have to enroll either as an individual or as an organization. For organizations it becomes a little bit more complicated from the legal side, but as an individual you only need an Apple ID with two-factor authentication enabled. 

<p align="center">
  <img src="https://github.com/JiriHoffmann/cis357-FinalProject/blob/main/images/entity_type_ASC.png?raw=true" />
</p>

An important note is that Apple charges \$99 yearly, which is much higher than Google's \$25 one time application fee. But just like Google, Apple will provide you with all the tools needed to get the app ready for production before having to register as a developer. 

Go to: **https://developer.apple.com/**, where you can read more about the benefits of being a developer. Once you are ready hit ***Enroll*** in the upper right corner to get started.

<p align="center">
  <img src="https://github.com/JiriHoffmann/cis357-FinalProject/blob/main/images/create_account_ASC.png?raw=true" />
</p>

First off you will have to fill out some basic information. Then, you have to select the entity type and then continue with the membership fee payment.

### App publishing

Once the registration process is complete, you are ready to start with the app publishing process. In order to do so, go to App Store Connect. Start with clicking on the `+` , then ***New App*** and fill out the information.

<p align="center">
  <img src="https://github.com/JiriHoffmann/cis357-FinalProject/blob/main/images/create_app_ASC.png?raw=true" />
</p>

If you don’t have a bundle ID click on the link and register a new App ID. Also, notice that ***User Access*** is meant for users within your organisation and not the app users. Once you hit ***Create*** a new app entry will be created. 


### Version Information


The main dashboard for the app will show up. The first step is uploading screenshots that will be used on the App Store. I recommend using the simulator with the following settings:

- *Pro Max version to take 6.5” screenshots*
- *iPhone 8 Plus for 5.5"*

They have the **exact** required resolution and any other screenshots will **not** be accepted without size adjustments. If the app supports iPads and looks different you should also include screenshots for them, but they are not required for the app submission only 6.5" and 5.5" must be included. 

<p align="center">
  <img src="https://github.com/JiriHoffmann/cis357-FinalProject/blob/main/images/upload_screenshots_ASC.png?raw=true" />
</p>


Next up there are a couple of text fields that provide basic information for the App Store listing and all of them should be pretty self explanatory. The ***Promotional Text*** will most likely not be used for the first release, but it is the only field that can be updated without requiring a new submission review.

### App Clip

App Clips are one of the newest additions to iOS, starting with iOS 14. They allow parts of the app to be opened without having to download the entire app. They can be invoked by App Clip codes that encode a URL and incorporate NFC tags, QR codes, or simply just messages and website links.

### iMessage App

This section is dedicated to apps that provide add-ons to the iMessage app like stickers and games.


### Apple Watch

Also self explanatory, this is where you upload apps for the Apple Watch.

### Build 

The uploaded app build will show up here. Apple provides multiple ways to upload but the easiest and most seamless one is through ***Xcode***. You can follow these steps:

1. In the top build menu select ***Any iOS device***

<p align="center">
  <img src="https://github.com/JiriHoffmann/cis357-FinalProject/blob/main/images/build_type_ASC.png?raw=true" />
</p>


2. Under Product select ***Archive*** and let Xcode build the archive.

<p align="center">
  <img src="https://github.com/JiriHoffmann/cis357-FinalProject/blob/main/images/archive_ASC.png?raw=true" />
</p>

3. Once it’s done a new window will pop up with all your archives for the app. Select the archive and click ***Distribute App***.
4. Select options and continue through the signing process
5. When that’s finished you should be able to refresh your ***App Store Connect*** page and the build will show up. (This might take a couple of minutes)

Uploading the archive will also allow you to test it out the release version of the app through ***TestFlight***. More information can be found in the dedicated tab at the top of the ***App Store Connect*** website.

### General App Information


Uploading the build will fill out some of the text fields like the version as well as add an icon for the App Store, the rest has to be filled out manually.

### App Review Information

An important step to get your app review approved. You will need to provide additional contact information in case there are any further questions during the review process. Also, if the app requires users to login you will have to provide some login credentials.

### Version Release

Just like Google, Apple provides developers with ***scheduled releases***, although Google allows more fine-tuning in this case. So this and following parts give you options to select when and how the new app/version will be released once the review is approved.

### Almost ready

Now that you have most of the submission form filled out, you will have to check some of the other tabs on the left side. For the first release, the most important one is ***App privacy***, as it is a requirement to provide a privacy policy. Then check out ***Pricing and Availability*** to select both country and device availability as well as pricing if the app is not free. With all these steps done you are most likely to submit the app. Hit the ***App Store*** tab and you should see a blue ***Submit for Review*** button. If you missed any parts you will see a red error box telling you what else you need to do. 

**And... That’s it!** 