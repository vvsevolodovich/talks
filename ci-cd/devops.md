slidenumbers: true
autoscale: true
build-lists: true

# Mobile: DevOps or not DevOps

---

# Такие чудеса, Гораций, не снились нашим DevOps-ам. 

![right](https://pbs.twimg.com/profile_images/932038471857848321/XcJ2nHhf_400x400.jpg)

---

# My self

* Vladimir Ivanov
* EPAM Systems

![right](photo.jpg)


---

# [fit]You

<!--

* run Lint/Static Analysis on the Code
* run Unit Tests
* maintain Build Numbers
* build the App from Code
* deploy the App 
* notify about status
* run e2e tests
* provide Logs, Artifacts & Build Reports
* and actually many more

---

![](https://media.giphy.com/media/BmmfETghGOPrW/giphy.gif)

-->

---

# Mobile Landscape

---

![](https://cdn-images-1.medium.com/max/1600/1*00pQn9OtMR1X95fikeOpcQ.gif)

---

![fit](https://cdn.auth0.com/blog/react-js/react.png)
![fit](https://seeklogo.com/images/X/xamarin-logo-348B1EB629-seeklogo.com.png)
![fit](https://cdn-images-1.medium.com/max/1200/1*5-aoK8IBmXve5whBQM90GA.png)

---

# DevOps Practices

* Continuous integration
* Continuous delivery
* Secured process
* Frequent releases(Canary/BG deployments)
* Automated testing
* Monitoring
* Automated rollback

---

# Alena

![right fit](image.jpeg)

---

# Continuous Integration

---

# Deploy

---

![fit](https://media.giphy.com/media/AWQyGGt1cOFt6/giphy.gif)

---

![fit](https://media.idownloadblog.com/wp-content/uploads/2018/01/Testflight-icon.jpg)
![fit](https://www.androidcentral.com/sites/androidcentral.com/files/topic_images/2016/new-google-play.png)
![fit](https://pbs.twimg.com/profile_images/1018995854181576704/E-nYFL4k_400x400.jpg)
![fit](https://techcrunch.com/wp-content/uploads/2013/05/logo-640.png?w=730&crop=1)
![fit](https://rollout.io/blog/wp-content/uploads/sites/2/2017/01/deploygate-Logo-2.png)
![fit](https://www.sqli-digital-experience.com/files/2014/06/logo-appaaloosa.png)

---

# Rollouts

* Internal testing, Alpha and Beta channels in Google Play
* Internal testing, Public Testing in TestFlight
* Public releases support staged rollouts

---

# [fit]Sign

---

# [fit]Secured process

---

![fit](https://tr2.cbsistatic.com/hub/i/r/2019/08/27/37a65923-bee5-4f2d-9df9-64a94f84d8a5/resize/770x/b1ead03fe8c27f7c50e213236ab172c1/android10hero.jpg)

---

![fit](https://developer.android.com/studio/images/publish/appsigning_selfmanagediagram_2x.png)

---

# Android Sign

* Keystore(Java Keystore)
* Store pass
* Key alias
* Key pass

---

![fit](https://www.midgard.co.uk/wp-content/uploads/2019/04/imap-Ios-Logo-Apple.png)

---

![fit](https://lh6.googleusercontent.com/_PCRgS2XUCt2hFJStwDr5fNg5SzC4BoT3D9_21uvIx8mNsP6zobU-DI-hfjNuJBxhgKJF6FZ0xJjOrb32us-Rvw6QNZf7vQUOdWYz4kOEJ_6ixCaTq5bYFcb2eK4WxEkPYt4NS6m)

---

![fit](this-is-fine.0.jpg)

---

# DevOps Practices

* Continuous integration :white_check_mark:
* Continuous delivery :white_check_mark: 
* Secured process :white_check_mark:
* Frequent releases(Canary/BG deployments)
* Automated testing
* Monitoring
* Automated rollback

[.build-lists: false]

---

# [fit]Review

---

# GP used to take 3-4 hours
# AppStore used to take 2 weeks

---

# GP takes 3-4 ~~hours~~ days
# AppStore used to take 2 ~~weeks~~ days

---

# DevOps Practices

* Continuous integration :white_check_mark:
* Continuous delivery :white_check_mark:
* Secured process :white_check_mark:
* Frequent releases(Canary/BG deployments) :white_check_mark:
* Automated testing
* Monitoring
* Automated rollback

[.build-lists: false]

---

# e2e tests

---

![fit](https://media.giphy.com/media/qc1waqAag4tZC/giphy.gif)

---

# Issues e2e tests

* Takes a lot of time
* Requires devices

---

# How to cope with devices?

* Buy our own(expensive)
* Test on Emulators(bad quality)
* Device Farms

---

![fit center](https://i.pinimg.com/originals/43/4c/9d/434c9dc6a1d566a41367976336d296cc.jpg)

---

# Device Farms

* AWS Device Farm
* Firebase device farm
* Azure Device Farm
* Others
* Your own

![fit right](https://appinventiv.com/blog/wp-content/uploads/2017/03/Android-App-With-Espresso-And-AWS-Device-Farm.png)

---

# [fit]Building your own

---

# What would you need

* Web Server
* Logs Storage
* Devices
* Media to connect to the devices(add, xcrun)

---

# Easy part...

* List of devices

	`$ adb devices`
	`$ xcrun simctl list`

---

![fit](https://shashikantjagtap.net/wp-content/uploads/2017/06/simctl_list.gif)

---

# Easy part...

* List of devices

	`$ adb devices`
	`$ xcrun simctl list`

* Installation and uploading files

	`$ adb push selfie.png /sdcard0/Downloads`
	`$ adb install -r myCoolApp.apk`
	`$ xcrun altool --upload-app --type ios --file "path/to/application.ipa" --username "YOUR_ITMC_USER" --password "YOUR_ITMC_PASSWORD"`

---

# Complex thing

* Streaming

	Android: adb, scrcpy[^2] tool
	iOS: xcrun

[^2]: https://blog.rom1v.com/2018/03/introducing-scrcpy/

---

![fit](farm.png)

---

# In EPAM

* Mobile farm for Mobile CC
* Free for the projects at the moment
* Plans for commercial offerings

![right](epamfarm.png)

---

# DevOps Practices

* Continuous integration :white_check_mark:
* Continuous delivery :white_check_mark:
* Secured process :white_check_mark:
* Frequent releases(Canary/BG deployments) :white_check_mark:
* Automated testing :white_check_mark:
* Monitoring
* Automated rollback

[.build-lists: false]

---

![fit](observability.jpeg)

---

# Observability

* Mobile apps run on the user devices and deployed through stores which make them unmanageable
* However observability is still in place

---

# Crash Reporting and Analytics

* Your own(with help of ACRA)
* Firebase Analytics
* AppCenter
* Sentry 
* Bugsnag

---

# What can be gathered

* Free device memory
* Free process memory
* Device, OS Version
* Active users
* Session lengths
* Thread dump
* Stacktrace
* Many more

---

![fit](https://miro.medium.com/max/4314/1*_5wcs9zDLHMWM3g69mKGPg.png)

---

# Martin

![fit right](Martin.jpeg)

---

![fit](https://koenig-media.raywenderlich.com/uploads/2018/09/ProGuardCrash1.png)

---

# Compilation/Obfuscation, my ass

---

![fit](https://i.imgflip.com/3erfav.jpg)

---

![fit](https://developer.apple.com/library/archive/technotes/tn2151/Art/tn2151_bitcode_overview.png)

---

![fit](https://miro.medium.com/max/3552/1*2wsimRFo3i2Ro-Fcpb_kyA.png)

---

![fit center](https://www.e-nor.com/wp-content/uploads/2019/06/firebase-project.png)

---

![fit center](https://www.e-nor.com/wp-content/uploads/2019/06/firebase-project-bts.png)

---

# AppCenter

---

![fit center](https://docs.microsoft.com/en-us/azure/azure-monitor/app/media/app-insights-overview/diagram.png)

---

# DevOps Practices

* Continuous integration :white_check_mark:
* Continuous delivery :white_check_mark:
* Secured process :white_check_mark:
* Frequent releases(Canary/BG deployments) :white_check_mark:
* Automated testing :white_check_mark:
* Monitoring :white_check_mark:
* Automated rollback

[.build-lists: false]

---

# Unfortunately

---

## No rollbacks of unsuccessful releases  

---

## You need to build a new version and deploy it instead

---

![fit](https://tr3.cbsistatic.com/hub/i/r/2017/09/13/b0d7b177-6593-42c2-924b-5df1980aef42/resize/1200x/5824f2cd6ec26e8dfc477fd1f1b39757/saddeveloper.jpg)

---

# Possible solutions

* Feature flags and server configs
* Usage of React-Native or other js based technologies 

---

# DevOps Practices

* Continuous integration :white_check_mark:
* Continuous delivery :white_check_mark:
* Secured process :white_check_mark:
* Frequent releases(Canary/BG deployments) :white_check_mark:
* Automated testing :white_check_mark:
* Monitoring :white_check_mark:
* Automated rollback :x:

[.build-lists: false]

---

# Caveats

---

# Hardware

* Android can be built anywhere
* iOS - only on Mac machines

---

# Long buildtimes

![fit](https://media.giphy.com/media/qc1waqAag4tZC/giphy.gif)

---

# How to fight long build times

* Identifying slow code parts
* Caching dependencies
* Modularization
* Build systems hacks
* And more[^10]

[^10]: https://medium.com/@joshgare/8-tips-to-speed-up-your-swift-build-and-compile-times-in-xcode-73081e1d84ba

---

# Caching

---

# iOS

* CocoaPods
* Carthage
* SwiftPM

---

# iOS

* CocoaPods - source code based, own build spec
* Carthage - dynamic frameworks
* SwiftPM - built by Apple
	- no resources support
	- single language per package
	- problems having binary deps

---

# Android

* Gradle
* Bazel/BUCK for companies with BIG apps

---

![fit center](cache.png)

---

## React-Native doesn't benefit from caching

---

## But does benefit from building two apps within a single run

---

![fit center](rnapp.png)

---

* Checkout the code
* Install the dependencies
* Compile Android
* Compile iOS
* Sign both
* Deploy both

---

* Checkout the code
* Install the dependencies
* ~~Compile Android~~
* ~~Compile iOS~~
* ~~Sign both~~
* ~~Deploy both~~

[.build-lists: false]

---

## Modularization

---

![fit center](buildtime.png)

---

# How to start

./gradlew clean assembleDebug --scan

---

# Gradle 

* Takes 1 minute to configure 1300 modules
* Due to IO and unlimited immutability

---

# Bazel

See the talk of Artem Zinnatullin[^1]

![right](zinnatullin.png)

[^1]:https://www.droidcon.com/media-detail?video=362742329

---

## Your CI/CD pipeline should support it all!

---

# Approaches

---

# Approaches

* Install Jenkins/TeamCity/Whatever else
* Spawn a Jenkins VM/Container in a Cloud
* Use SaaS 

---

# Local Jenkins

* Free
* Great flexibility
* Agents system
* Decent plugin system
* For iOS: just install an agent on a Mac
* But no containerization out-of-the-box
* All support burden is on your shoulders

![right](https://cdn-images-1.medium.com/max/1200/1*RmcSmwPhUn8ljLiiwYxK0A.png)

---

## It should be managed

---

![fit center](https://docs.fastlane.tools/img/fastlane_text.png)

---

![fit center](https://i.kinja-img.com/gawker-media/image/upload/s--IL3ZHXoY--/c_scale,f_auto,fl_progressive,q_80,w_800/mloqbklwwmtzjxiajmr2.jpg)

---

![fit center](https://docs.fastlane.tools/img/actions/sighRecording.gif)

---

# Pros


✨	More than 400 integrations
📖	100% open source under the MIT license
⚒	Runs on your machine, it's your app and your data
🖥	Supports iOS, Mac, and Android apps
🔧	Extendable


---

# When

* For education purposes and student projects
* For companies which already use Jenkins
* For security paranoids(debatable) 


![right](https://cdn-images-1.medium.com/max/1200/1*RmcSmwPhUn8ljLiiwYxK0A.png)

---

# Jenkins in Cloud

* Solves the containerization issue
* Support burden is partially decreased
* Unclear how to solve Mac issue

---

# 3rd party services

---

# 3rd party services

* GitLab CI
* Circle CI
* Nevercode
* App Center
* Bitrise

---

# GitLab CI/Circle CI

* Very basic support(mac machines, xcode, gradle)
* Integration with the parent tool 
* Yaml editor as an interface
* Almost no mobile specific involved

---

# App Center

![right](https://pbs.twimg.com/profile_images/1018995854181576704/E-nYFL4k_400x400.jpg)

---

# App Center - Azure DevOps

* Part of the integrated environment(former TFS)
* Distribution destinations - GP, TestFlight, Internal
* Bitbucket, Github, VSTS, GitLab(!)
* Configuration as Code :white_check_mark:
* Mobile Apps as first class citizens :white_check_mark:
* Cloud based :white_check_mark:
* Allows for Machine Pools(which solves Mac issue)
* Webhooks

---

# App Center - Azure DevOps

* Support for ad-hoc git servers :x:
* SonarQube Support - :x:
* Local debug - :x:

---

# App Center - When

* You already have Azure DevOps/Azure subscription
* You're hosted in Bitbucket/Github
* You only want apps distribution solution

---


![](https://d2mn9dr0jv4622.cloudfront.net/wp-content/uploads/2017/09/19105203/nevercode1.png)

---

# Nevercode

* Mobile Centric CI/CD
* Distribution destinations - App Store Connect, Google Play, HockeyApp, Crashlytics, TestFairy
* Bitbucket, GitHub or GitLab
* Cloud based :white_check_mark:
* Mobile Apps as first class citizens :white_check_mark:
* Webhooks :white_check_mark:

---

# Nevercode

* Configuration as Code :x:
* Pricy :x:

---

# Nevercode - When

* Flutter apps

---

# Bitrise

* Mobile Centric CI/CD
* Distribution destinations - GP, TestFlight, TestFairy, App Center, Whatever
* Bitbucket, Github, Custom
* Configuration as Code :white_check_mark:
* Mobile Apps as first class citizens :white_check_mark:
* Cloud based :white_check_mark:
* Webhooks

---

# Bitrise

* Support for ad-hoc git servers :white_check_mark:
* Support CI job triggers on push to Any branch :white_check_mark:
* SonarQube Support with a community extension :white_check_mark:
* Local debug - :white_check_mark:
* Open source

---

![](bitrise.png)

---

# Bitrise

* Rather slow :x:
* No Flutter support(yet) :x:
* Flutter support(already) :white_check_mark:

---

# Services Comparison

| App Center | Nevercode | Bitrise |
| --- | --- | --- |
| Simplicity :white_check_mark: | Flutter :white_check_mark: | Flexible :white_check_mark: |
| Device Cloud :white_check_mark: | Build cache :white_check_mark: | Build cache :white_check_mark: |
| Crash Reporting :white_check_mark: | No Xamarin :x: | Different inf. stacks :white_check_mark: |
| Difficult customization :x: | No conf as service :x: | Open Source :white_check_mark: |
||Funny jokes |Slow :x:|

---

![fit](https://media.giphy.com/media/kVaj8JXJcDsqs/giphy.gif)

---

# DevOps Practices

* Secured process :white_check_mark:
* Continuous integration :white_check_mark:
* Continuous delivery :white_check_mark:
* Frequent releases(Canary/BG deployments) :white_check_mark:
* Automated testing :white_check_mark:
* Monitoring :white_check_mark:
* Automated rollback :x:

[.build-lists: false]

---

# Summary

* Mobile is a serious business requiring automation
* There are some caveats and issues which are overcomeable
* Except rollbacks


---

![fit](https://media.glassdoor.com/l/dc/fc/8e/ee/epam-mexico.jpg)

---

# Links

* Twitter, telegram: @vvsevolodovich
* Talks: http://speakerdeck.com/vlivanov
* Email: Vladimir_Ivanov4@epam.com 
* https://mobiusconf.com/

![right](photo.jpg)

