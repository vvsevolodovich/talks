footer: *<EPAM>*
slidenumbers: true
slidecount: true
autoscale: true
build-lists: true
slide-transition: true

![](https://cdn.instructables.com/FO4/IKQW/IWCFDIYU/FO4IKQWIWCFDIYU.LARGE.jpg)

---

# About me

* Vladimir Ivanov
* Designing Mobile-centric solutions for living
* Primary Skill: Android
* Certified Google Cloud Architect.

---

# About me

* Vladimir Ivanov
* Designing Mobile-centric solutions for living
* Primary Skill: Android
* Certified Google Cloud Architect.

![fit right](https://lh3.googleusercontent.com/rZX1OsIg2mzwDyS1t6zddh_3wyWkPEMNkMkGYGQtLgSvtqmjr20r087zpe8y77wqkHOyiozFPokt43ur349NY1XXfgWagVG7Vh2BOkxUrHRyxVJTz0gETBzAiwsQVAMsjkkh9K-yp3tzqZJcAeTYJGMLhAiuBcYe-dMggpnaFH91LhgbEOu98GNo5MiwXFABv8GTvGoU7Chk4GgUBRJ9FuNtMN77kKrS7IfGR0GLJh4rzBEUp0iyzLiqISckMHSwtBufyOdRj9Vzjwt1xq9d0S3b7JMZP_gwEReR6yWV_hzuWYz9g19M4E21YGc6GatQI9LbYUgPf3jpabka_fpLgCtVkbaEyrwUtZ5leJrUzVJe41otzMQ5zOXmw1JVmmL5SgSVhYikx2KKilxWeYm5q5XXdvj9V6TyWiGBXsnAd4HQqKxopOIeXodVOf9zufcJTcWlkUbZA5Uy36qypIQodWUID7Fm4HtGdE8c5BxPWK37aZfgh3GKDEUkj00XkAVOGXIN6OW5lAkhnxDqA6uNrxWuKwiFeDJwVH7lpAEqAr-0_VxKW09G6aq-1kT_2ineaEF6oJeG37s_Yw7-2BQowroQ_7hDnTE1E6_x6cvYRLAGp2SVBIqKsXqY2VUmpR8QAqU94vvOSbhPm9PoM9sUq6vN7CcPKio=w1222-h1628-no)

[.build-lists: false]

---

# Reality Check

![fit](https://www.esquireme.com/sites/default/files/styles/full_img/public/images/2017/05/01/landscape-1493413857-the-matrix.jpg?itok=INZP60C1)


---

# What is IT-Industry?

* The sum of companies providing information and data based products and services added by IT-departments of other companies[^1].

[^1]: My own definition

---

# What is great about our industry?

* We are growing despite Brexit, the US - China trade wars and others[^2]
* The developers are paid far from minimum wages(90k vs 19k) [^3]
* The remote style is conquering the world

[^2]: https://www.gartner.com/en/newsroom/press-releases/2019-01-28-gartner-says-global-it-spending-to-reach--3-8-trillio

[^3]: https://habr.com/en/company/moikrug/blog/420391/

---

# However

![original](http://reframe.sussex.ac.uk/post-cinema/files/2016/03/Figure_01_Desert-of-the-real.png)

---

# However

* Security is a disaster
* Quality is a concern
* Inclusivity is a not heard of

![original](http://reframe.sussex.ac.uk/post-cinema/files/2016/03/Figure_01_Desert-of-the-real.png)

---

# Security

---

# Security

* Data breaches potentially affected __> 1 billion users in 2018__
* New breaches happen literally every day
* Mobile application security is a big concern since 2011


---

![fit](https://lh5.googleusercontent.com/gRKGofzcQapwG8LHtyN07P2w9dHUBBkyDjOoTL2aYmkIE7p68nhEkJZJTqEg0lJtaXPwZCDjVZ5SjHCy66eOJ4Qe-j6MU2rxVIoDwaGsqgM0nrCQ0dcWURoeNpOHO8GVzrZo_tjM)

---

![](n26.png)

---

# N26

* Same app for verification
* Exposed secret information in the API
* No notification about secrets changes
* All powerful Support

---

# Luckily everything is fixed, but impression...

---

![fit](jcenter.png)

---

# What happened?

* Audio recording library was asking for INTERNET permission
* Turns out the library was altered and put to jcenter
* Sends device analytics to some server

---

# Firebase misconfiguration

* __2.6 million__ plaintext passwords and user IDs
* __4 million+__ PHI records
* __25 million__ GPS location records
* __50,000__ financial records including banking, payment and Bitcoin transactions
* __4.5 million+__ Facebook, LinkedIn, Firebase, and corporate data store user tokens.

---

![fit](googleplay.png)

[^googleplay]: https://bgr.com/2018/11/25/google-play-store-apps-removed-malware-found/

---

# Vulnerabilities in Android

* Download provider allows for accessing all downloads(which can be used to hijack OTA update)
* Accessing protected data(like CookieData)[^7]

[^7]: https://ioactive.com/multiple-vulnerabilities-in-androids-download-provider-cve-2018-9468-cve-2018-9493-cve-2018-9546/

---

# IoT

![original](http://reframe.sussex.ac.uk/post-cinema/files/2016/03/Figure_06_Neo-as-a-Cyborg.png)

---

Top IoT hacks of 2018[^3]

* Mirai Botnet
* Jeep car hijacking
* Owlet wifi Heart Monitor for Babies

[^3]: https://www.iotforall.com/infamous-iot-hacks/

---

# You can actually steal a Tesla with just a range extender![^4]

* Now the car requires a PIN, but impression...

[^4]: https://www.theverge.com/2018/10/22/18008514/tesla-model-s-stolen-key-fob-hack-watch-video

---

![fit](http://sailormoonnews.com/wp-content/uploads/2017/03/the_matrix_pods_of_humans.jpg)

---

# Conclusion #1: We don't pay enough attention to the security.

---

# Quality

---

![fit](businessinsider.png)

---

# Business insider

* Two popups
* 25% of content is visible
* The page restarts on accepting cookies
* Debug output on the page

![fit right](businessinsider.png)

---

# Bank Saint-Petersburg

* Used to crash everyday on Android 9
* Still has no biometric authentication
* Used to miss push notifications and transaction details

---

# Twitter App

* Newsfeed still lags on Samsung S9
* 8 cores are still not enough for twitter for smooth scroll!

---

# Some programmer stuff...

---
	
![fit original](https://pbs.twimg.com/media/D-Il5gfXYAI58Wa.jpg:large)

---

# Conclusion #2: Our apps are unstable, slow, creepy looking, lack functionality or become incredibly complex.

---

# Inclusivity 

---

![fit](https://www.youtube.com/watch?v=YJjv_OeiHmo)

---

# If you lack diversity in your product teams, you're unable to build proper products

---

# Terms

* Inclusivity - ability of a group to include different people
* Diversity - property of a group including different people

---

# Gender diversity

* Because it affects everybody.
* It's not about social justice, wage gap, etc.

---

# Some stats

* Women occupy __7%__ of programming jobs in Russia, __20%__ in USA[^5]
* Stackoverflow.com audience is only __9%__ women [^6] 

[^5]: Different sources, like https://www.ncwit.org/sites/default/files/resources/womenintech_facts_fullreport_05132016.pdf , https://habr.com/en/company/moikrug/blog/329018/

[^6]: https://insights.stackoverflow.com/survey/2019#demographics

---

# More stats...


One large-scale study found that after about 12 years, approximately __50 percent of women had left their jobs in STEM fields—mostly in computing or engineering (Glass, Sassler, Levitte & Michelmore, 2013)__. As Figure 1.6 indicates, only about 20 percent of women working in other non-STEM professional occupations left their fields during the 30-year span covered by the study. Women in STEM also were more likely to leave in the first few years of their career than women in non-STEM professions.[^6]

[^6]: https://www.ncwit.org/sites/default/files/resources/womenintech_facts_fullreport_05132016.pdf

---

# Somehow we push away women

---

![fit](vixentael.png)

---

![fit](nazarov.png)

---

# Conclusion #3 : Despite having insufficient developers we push away a group with most potential, which is plain stupid

---

# Conclusion #3 : Despite having insufficient developers we push away a group with most potential, which is plain stupid

BTW, there are agism, race prejudice and other problems, but gender is a worldwide thing. 

---

# Life is Suffering

---

# Amusement?

![original](https://memegenerator.net/img/images/11831055.jpg)

---

# Responsibility

![](https://i.stack.imgur.com/lfgUA.png)

---

# So

* Get ownership for your product
* Standup for quality, security, inclusivity and other issues
* Learn 
* Make the world around you a better place, at least not worse

---

![fit](https://cdn-images-1.medium.com/max/1200/1*q6sHPDrdrQPmzCAbR0I4Dw.jpeg)

---

---

![fit](10xengineer.png)

---

# If it's not enough...

https://tonsky.me/blog/disenchantment/

---

# Those are the problems of the industry.

Ask yourself: do want to be treated as not a brilliant engineer because you have a work schedule?
Do you want your female coworker treated unrespectfully on a conference? 
Do you want your data downloadable in a public telegram channel? 

---

# Slay a dragon![^10]

[^10]: https://en.wikipedia.org/wiki/Princess_and_dragon

---

# But how?

---

# You make yourself strong, and knowledge and skill is your sword.

---

# Get to know the enemy 

---

# Pass a security training

* https://training.cossacklabs.com/
* https://asap.kaspersky.com/en/

---

# Read a damn book!

* Serious Crypto от @veorq
* Cryptography Engineering от @schneierblog

---

# Attend to a damn course!

* On udacity for example[^11]

[^11]: https://www.udacity.com/course/applied-cryptography--cs387

---

# Encourage women

* Cut the unacceptable behavior
* Give women voice
* Help WomenWhoCode, WomenInTech, InfluenceHER and other communities

---

# Fight for quality

* Require a UX engineer
* Use dogfooding
* Do not hesitate to object

---

# Attend to a damn course!

* In Udemy for example[^12]

[^12]: https://www.udemy.com/sketchdesign/?altsc=381850

---

# Me

* https://twitter.com/vvsevolodovich :bird:
* https://medium.com/@dzigorium :pencil:

![right](me.jpg)

