footer: EPAM Systems
slidenumbers: true
slidecount: true
autoscale: true
build-lists: true

# Role of a Solution Architect in a Software Project

---

![fit](https://pbs.twimg.com/media/CcdX-dlWAAAJ0SW.jpg)

---

# About me

* Vladimir Ivanov
* Working as a Solution Architect
* Certified Google Cloud Architect
* Speaker
* PC of Mobius

---

# Let's get to know each other!

---

# What is the motivation of our work?

---

# Helping business to grow by solving their problems with technology

---

# The way we do it is completing projects

---

![center](project.png)

---

# RFI

## Request for information

---

# RFI

* Answer the questions
* Contact the architects of related fields
* Perform the required research

---

# RFP

## Request for proposal

---

# RFP

* Understand the business value 
* Create a solution architecture
* Understand which teams are necessary to implement that solution 
* Come up with the resource plan
* Present a proposal

---

![center](project.png)

---

# Discovery

---

![fit](https://lh3.googleusercontent.com/OJ245rNhbZgu6paL6esd7wa2EjEg2LEtxU6oY5YQV0Xd4NDzmeb8osM96szFgfFQYSBMI6aYTqxdu-b8nndowu7l6M-xR-wP9hQpAdDvsxOFrh4x868S8kaZXRSAjDI01GZUvSL4J8HYln-0W4dR89OPj33VQDFiox-M3Us9eK6tjpIyhz7ZYMU5GQYry85099vXw0lPmgFu5fiRtYh3CByxM5CelTHiNlxBGJ1oCT5Ihx2Tsr4MTTF_I8WxXMq1CYt498YlxHLBxi_8nMy8SO5PrZX-E3eq4bFsKz_4hHENk3Q_GeodQuuQeJh1U3hFpOXHV2a2JlUorRBALsEVnhutsCGvoKlZoLeDiSP5UAdb9glImIs_sUAZqEN4-fEUsNfc_ekYam_8XUBEl32pTGrHeuTpZHI8MASqQFyYxWb7VpVdVb0t_4Z2INHkDrmpUAwZCUsRKFu-hm1w5SBUaWw8MOcfdY_EVC1sZbglCyUIzkuYZffEreSg1oAztnQu2v-ZyAPlJoAinEqHp0hRPNLWDEM1ccyx7_VAZBHAa6gk2SsKBbkMT2-8YuLBEUkro7I-AA8suJAnSHZhpGogUN7Sbf89ruq5OibGrCd1Sq6qNZvvtEWiqVfIiYMAgyZjxf2zSHeneT_dkfABluOmD7NkUthIm30M_kORJxQyOTqUnhIYhWuEpDc=w2008-h1506-no)


---

# First steps

* Getting to know the organization and key people
* Getting to know the business and it's goals
* Build trust

---

# Requirements gathering

* Functional
* Non-functional
* Constraints

---

# Functional requirements!

* The system should allow an administrator to login
* The system should show the list of users

---

# Non-functional requirements

* The application should use TLS 1.2 for all connections involving user-data
* The application should open the page under 0.5 second
* The application may not be available 1 hour per year 

--- 

# Constraints

* The app should be deployed to customers' Azure cloud
* The app should implement 152 federal law
* The app should be developed with Xamarin technology

---

# Some of them will change the architecture of the solution.

---

# Every additional 9 of availability doubles the complexity of a target system.

---

![fit](cost.png)

---

# Source of requirements

* Stakeholders

---

Stakeholders are the people who have an interest in the project

* Customer business representatives
* Delivery organization business representatives
* Technical folks from both sides
* End-users
* Competitors

---

## In order to gather requirements you need to talk to stakeholders. 

## The stakeholders identification is one of the main responsibilities of a Solution Architect.

---

![fit](https://lh3.googleusercontent.com/kW8Ax5vY5VnOPIQW1J34JvINdhdEtWmZN436TPaTiehpkpEowQYT4Y9wbcHcUrJIxYMnsu4fcQ0Pk7ktjDbmdGWQfjFChv7hE4LvWIp3tlZltln8RfD7WreWFbJgwztWLoxtvEABKLPtCLQjbktbJQLNo1FKkgKAo9qlE8-Bp1DdMATiDDdRiXNEc9iqVOCC11Ps1x-CQTq5K1zeMu4fdpPuArPKbnE9vEePUt2K7ZjI1klWbCNdrI4ZeRyaEE2B7MoWoBCaiyKNrWATH2Gk5IhD-vwXQuUZx4QQzMCJTlKYWYbmv5a6Oeu4Z7cYjn07fJFeELwMnLRKQmUVM79F_DiPfXDzvc9d0MIkufIHxDvPQJskeAWGlYl34j5tuMUmxNVxaWgEnE02Enpa8eFKu47U7ZBTQkv6In-rhbbVp4tzMlZg-JBCVZhvDBKzL-esuIrosceDAw67dC0nh65MU2CZZSsQFFO839_4Knja-zjy5W6eS5lva_rGsEX3ukDqFj9brohPj5c701ztIAWdpqJFeVjhx-v5eXUChe9hkJlVRbVQK4api1uU0aiUJYhx51gfXxtHReiPmrjrCVdytjKI5aRqzys7VYNgnl55kbQxpiW95t9CKQF7GJTK2jlHIJ6aiRFDclRV2F6MlZ1LgzPYX7RGqX4paasLePW79YgNcDiAOFXlxss=w2008-h1506-no)

---


# What’s an architecture? 

The set of structures needed to reason about the system, which comprises software elements, relations among them, and properties of both. [^2]


[^2]: 
 	Software Architecture in Practice, 3rd Edition, Bass, Clements, Kazman, Addison-Wesley

---

# What the hell it means? 

* Architecture is a key to the system properties, an end user is concerned about
* Or product owner thinks so
* There are no bad or good architectures; there are ones that fit the target system properties

---

# ASRs

## Target system properties which affects architecture are unsurprisingly called architecturally significant requirements.  

---

![fit center](glasses.jpg)

---

# How to identify ASR? 

* From requirements documents
* By interviewing stakeholders
* By understanding the business goals
* Utility tree!

---

# Utility tree

---

![](qualityattributes.png)

---

![original](qa2.png)

---


![fit](qa3.png)

---

# How to document architecture? 

* Non-formal notations with general purpose diagramming
* Semi-formal notations with standardized notation
* Formal notations with precise semantics

---

![fit](https://wiki.smu.edu.sg/is480/img_auth.php/c/c4/Solution_Architecture_Diagram.png)

---

![fit](https://upload.wikimedia.org/wikipedia/commons/b/b8/Policy_Admin_Component_Diagram.PNG)

---

![fit](component.png)

---

![fit](https://c4model.com/img/c4-overview.png)

---

# Documenting the architecture is the third most important activity for an SA.

---

![center](project.png)

---

# Construction

* Bootstrap the development
* Define and setup quality gates
* Create PoCs 
* Share knowledge

---

![center](project.png)

---

# Transition

* To production
* To other team

---

# So...

The person who identifies stakeholders, gathers ASRs, builds the architecture, shares it and bootstraps some of the systems components is usually called Solution Architect.

---

![fit](https://www.altexsoft.com/media/2018/04/Software-documentation-2-2.jpg)

---

![fit](https://media.glassdoor.com/l/dc/fc/8e/ee/epam-mexico.jpg)

---

# Links

* Books is Software Architecture:
	https://medium.com/@nvashanin/books-in-software-architecture-6ad974e524ce
* Amazon Cloud Architect Associate:
	https://www.udemy.com/aws-certified-solutions-architect-associate/
* Google Cloud Architect Professional:
	https://www.coursera.org/specializations/gcp-architecture

---

# Me

* https://twitter.com/vvsevolodovich :bird:
* https://medium.com/@dzigorium :pencil:
* https://mobiusconf.com/
* Vladimir_Ivanov4@epam.com

![right](photo.jpg)


