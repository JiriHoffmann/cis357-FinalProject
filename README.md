# CIS 357 - Final Project


Android


Create a developer account

Create the app


Now that we have created the app we are redirected to the dashboard, where we have access to all of the features and settings provided by the Google Play Console. On the dashboard we can see the “Set up your app” tab which is required to be completed before the app can be published.
App access

In the first step we have to let Google know if all users can access all of the app’s features or if some of them are limited with a registration or some other form of account creation mechanism. Apps with restricted access require a brief description on how to access the content.


##Content rating

Content rating is a short questionnaire about the content of the app. First the developer is asked one of the provided categories which best describes the functionality of the app. This will be followed by a couple of questions based on the category selected in the previous question and then we can see how the app will be rated in different countries.





Target audience

Before selecting the target audience, the Ads section has to be filled out. This is very simple as we just pick if the app will contain ads or not. Now just selected the targeted age categories and we should be done here.



News app

Here we just need to confirm if it’s a news app or not.



Select an app category

This tab focuses on discoverability of the app. We will adding a category where the app can be found and tags for searching as well as some additional contact information.


Store listing

This will be the most important part for users. Here we set up the listings, provide descriptions and screenshots for different screen sizes. There are some very specific requirements for image sizes so make sure to take a look at them before creating the images.


Once all these steps are done, we are almost ready to start publishing the app. Google also provides great ways to test the app with a limited number of users before it gets officially published so you should definitely check it out.














Publish your app on Google Play
First off we select countries where the app will be available	and then before we do anything else we need to generate a signed apk or Android app bundle.

Android app bundles are preferred over apk. Bundles allow Google Play to serve individual apks to users based on their device configuration such as processor architecture or assets depending on the screen resolution.


App singing

The way app signing works on Android is that developers have to generate a signing key and use it to sign the app. The key has to be consistent across the entire app’s lifetime to ensure all updates are coming from the same developers. This obviously caused many issues if the key was lost and Google decided to refactor how signing works. There is now an opt in feature which let’s developers sign the apk with their “upload key”. The “upload key” works the same way as the “signing key” but it’s only used to upload the app to Google Play. Google then generates its own signing key and uses it to re-sign the app and stores it in their database. The added benefit of this approach is that developers can generate a new upload key if lost and the app will remain signed with the same key. I recommend reading more on this topic at the following link.

https://developer.android.com/studio/publish/app-signing?authuser=1#generate-key


Generating a key

The easiest way to generate a key is by using Android Studio.

In the top bar go to: Build > Generate Signed Bundle/APK
Select Android App Bundle or APK and hit next
In the Key store path click on Create new…
Fill out all required fields and a new key will be generated
If your app is ready to build you can continue the walkthrough which will let you generate the app bundle or apk. 
The app bundle or apk will be generated in app/build/outputs/release or debug based on the previous selection
If you want to verify that the app was signed with the correct key go to your java folder and in jdk/bin run jarsigner -verify -verbose -certs app_name.apk or use the apksigner provided by Google


Uploading to Google Play

Now that we have generated a signed app, we can go back to the Google Play Console website. First, if you would like to let Google generate and store the signing key hit Continue and upload the .aab or .apk file. After that click on Review release. Next up, you can see all the errors and warnings for the current release. For example, my app uses the camera so I have to go back and add a Privacy Policy. If there aren’t any warnings you are and you are all set to hit “Start rollout to Production”. Be sure your app is ready to be released! This will send the app for a review to Google. Once the review is done you can finally publish the app and let other users download it!




App Store

In order to be able to share your apps on the App Store, each user has to join Apple Developer Program first. In order to do so you have to enroll either as an individual or as an organization. For organizations it becomes a little bit more complicated from the legal side, but as an individual you only need an Apple ID with two-factor authentication enabled. An important note is that Apple charges $99 yearly, which is much higher than Google's $25 one time application fee. But just like Google, Apple will provide you with all the tools needed to get the app ready for production before having to register as a developer. 

Go to: https://developer.apple.com/ where you can read more about the benefits of being a developer. Once you are ready hit Enroll in the upper right corner to get started.





First off you will have to fill out some basic information.











































Next, you have to select the entity type and then continue with the membership fee payment.

















App publishing

Once the registration process is complete, you are ready to start with the app publishing process. In order to do so, go to App Store Connect. Start with clicking on the “+”, then New App and fill out the information. 





















If you don’t have a bundle ID click on the link and register a new App ID. Also, notice that User Access is meant for users within your organisation and not the app users. Once you hit Create a new app entry will be created. 


Version Information


The main dashboard for the app will show up. The first step is uploading screenshots that will be used on the App Store. I recommend using any Pro Max version of the simulator to take 6.5” screenshots and iPhone 8 Plus for 5.5” as they have the exact required resolution and any other screenshots will not be accepted without size adjustments. If the app supports iPads and looks different you should also include screenshots for them, but they are not required for the app submission.

Next up there are a couple of text fields that provide basic information for the App Store listing and all of them should be pretty self explanatory.

App Clip

App Clips are one of the newest additions to iOS, starting with iOS 14. They allow parts of the app to be opened without having to download the entire app. They can be invoked by App Clip codes that encode a URL and incorporate NFC tags, QR codes, or simply just messages and website links.

iMessage App

This section is dedicated to apps that provide add-ons to the iMessage app like stickers and games.



Apple Watch

Also self explanatory, this is where you upload apps for the Apple Watch.

Build 

The uploaded app build will show up here. Apple provides multiple ways to upload but the easiest and most seamless one is through Xcode. Once you are ready go to Xcode and follow these steps.

In the top build menu select Any iOS device



Under Product select Archive and let XCode build the archive.











 



 

 

Once it’s done a new window will pop up with all your archives for the app. Select the archive and click Distribute App.
Select options and continue through the signing process
When that’s finished you should be able to refresh your App Store Connect page and the build will show up. (This might take a couple of minutes)

Uploading the archive will also allow you to test it out the release version of the app through TestFlight. More information can be found in the TestFlight tab at the top of the App Store Connect website.

General App Information


Uploading the build should fill out some of the text fields in this tab as well as add an icon for the App Store, the rest has to be filled out manually.

App Review Information

An important step to get your app review approved. You will need to provide additional contact information in case there are any further questions during the review process. Also if the app requires users to login you will have to provide some login credentials.

Version Release

Just like Google, Apple provides developers with scheduled releases, although Google allows more fine-tuning in this case. So this and following parts give you options to select when and how the new app/version will be released once the review is approved.

Almost ready

Now that you have most of the submission form filled out, you will have to check some of the other tabs on the left side. For the first release, the most important one is App privacy, as it is a requirement to provide a privacy policy. Then check out Pricing and Availability to select both country and device availability as well as pricing if the app is not free. With all these steps done you are most likely to submit the app. Hit the App Store tab and you should see a blue Submit for Review button. If you missed any parts you will see a red error box telling you what else you need to do. That’s it! 


