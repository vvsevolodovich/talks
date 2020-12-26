slidenumbers: true
autoscale: true
build-lists: true

# Mobile CI/CD in 2K19

---


* Vladimir Ivanov
* EPAM Systems
* Mobius Conf

![right](photo.jpg)

---

![](http://archive.massappeal.com/wp-content/uploads/nas_star_wars_crawl_lead1.jpg)

---

![](https://laughingsquid.com/wp-content/uploads/DSC00505s.jpg)

---

![](android.mp4)

---

![](https://media.giphy.com/media/9HtiqxqYSUg6I/giphy.gif)

---

# CD

---

![](https://media.giphy.com/media/cFkiFMDg3iFoI/giphy.gif)


---

![](https://media.giphy.com/media/s0ifN6w2c4wJW/giphy.gif)

---

![](https://media.giphy.com/media/xT9IgH6tFP7dNVrQAw/giphy.gif)

---

# CI

---

# What do we love?

---

# Write code!

---

# What we dislike?

---

# Everything else!

---

# But still

* Code Quality
* Customer Transparency
* Developer Satisfaction 

---

# It is important!

---

# What should be done

---

* run Lint/Static Analysis on the Code
* run Unit Tests
* maintain Build Numbers
* build the App from Code
* deploy the App 
* notify about status
* provide Logs, Artifacts & Build Reports
* and actually many more

---

![](https://media.giphy.com/media/BmmfETghGOPrW/giphy.gif)

---

![fit](https://media1.giphy.com/media/3oEjHWbXcpeKhTktXi/giphy.gif?cid=3640f6095c8e5b6470434a345912d1be)

---

# Source code

---

# Source code

* Checkout from where?
* How to build?
* How to test?

---

# Checkout

---

# Git hostings

* Saas: Github, Bitbucket, Gitlab, Azure DevOps, AWS CodeCommit
* On-premise: Github Enterprise, Gitlab, Bitbucket Server
* Ad-Hoc

---

* Checkout different branches
* Trigger different builds on VCS commit/pull request
* Report build status to a VCS back

---

# Why it is important?

---

![fit](govnokod.png)

---

* Eslint
* swiftlint
* Java/Kotlin linters
* FindBugs

---

# Precommit hooks

---

![fit](no-verify.png)

---

## Validate code base on pull request/push

---

# Build

---

![](https://cdn-images-1.medium.com/max/1600/1*00pQn9OtMR1X95fikeOpcQ.gif)

---

![fit](https://cdn.auth0.com/blog/react-js/react.png)
![fit](https://seeklogo.com/images/X/xamarin-logo-348B1EB629-seeklogo.com.png)
![fit](https://cdn-images-1.medium.com/max/1200/1*5-aoK8IBmXve5whBQM90GA.png)

---

# Build should be 

* Reliable (isolated&clean)
* Fast (on performant machines)
* Locally reproducible (to debug)
* Customizable (for envs or other params)
* Secure (only allowed persons to create/edit/run builds)

---

# Sign

* Secure storage for provisioning profile/signing certificate/keystore
* Secure storage for password
* Account storage for pushing to Google Play/Test flight/3rd party services

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

# Deploy

* Connect to distribution services
* Manage upload secrets

---

# Testing

---

![](https://www.leadingagile.com/wp-content/uploads/2017/03/works-on-my-machine.jpg)

---

# Testing

* Unit/Module tests
* e2e tests

---

# Issues e2e tests

---

![fit](https://media.giphy.com/media/qc1waqAag4tZC/giphy.gif)

---

# Issues e2e tests

* Takes a lot of time
* Requires devices

---

# Miscellaneous

* Configuration as code
* Debug locally
* Centralized user management(SSO)
* Auto-configuration
* Extensions

---

## Your CI/CD pipeline should support it all!

---

# Approaches

---

# Approaches

* Install Jenkins/TeamCity/Whatever else
* Spawn a Jenkins VM/Container in a Cloud
* Use Saas 

---

# Local Jenkins

* Free
* Great flexibility
* Agents system
* Decent plugin system
* But no containerization out-of-the-box
* All support burden is on your shoulders


![right](https://cdn-images-1.medium.com/max/1200/1*RmcSmwPhUn8ljLiiwYxK0A.png)

---

# When

* For education purposes and student projects
* For companies which already use Jenkins
* For security paranoids(debatable) 


![right](https://cdn-images-1.medium.com/max/1200/1*RmcSmwPhUn8ljLiiwYxK0A.png)

---

# Jenkins in Cloud

* Solve the containirazion issue
* Support burden is partially decreased

---

# 3rd party services

---

# 3rd party services

* Circle CI
* GitLab CI
* Nevercode
* App Center
* Bitrise

---

# 3rd party services

* ~~Circle CI~~
* ~~GitLab CI~~
* Nevercode
* App Center
* Bitrise

[.build-lists: false]

---

# App Center

![right](https://pbs.twimg.com/profile_images/1018995854181576704/E-nYFL4k_400x400.jpg)

---

# App Center - Azure DevOps

* Part of the integrated environment(former TFS)
* Distribution destinations - GP, TestFlight, Internal
* Bitbucket, Github, VSTS 
* Configuration as Code :white_check_mark:
* Mobile Apps as first class citizens :white_check_mark:
* Cloud based :white_check_mark:
* Webhooks

---

# App Center - Azure DevOps

* Support for ad-hoc git servers :x:
* Support CI job triggers on push to Any branch :x:
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

---

# Conclusions

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

# Links

* https://twitter.com/vvsevolodovich :bird:
* https://medium.com/@dzigorium :pencil:
* https://mobiusconf.com/
* Vladimir_Ivanov4@epam.com

![right](photo.jpg)

