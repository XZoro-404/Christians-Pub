## Introduction  
---  
### Information  
This room focuses on the Software Development Lifecycle (SDLC) framework, its phases, and components. Learning objectives In this room, you will learn the following: 
- Understand the SDLC framework, what it is, and why it's important
- Learn about the phases of SDLC
- How to instil security into the SDLC
- Understand the Security SDLC phases and process  
### Questions  
  
*I'm ready to start!*  
  
>[!question]- **Answer**  
>  No answer needed!
## SDLC  
---  
### Information  
﻿What is Software Development Lifecycle (SDLC)?﻿The Software Development Lifecycle is a set of practices that make up a framework to standardize building software applications. SDLC defines the tasks to perform at each software development stage. This methodology aims to improve the quality of the software and the development process to exceed customer expectations and meet deadlines and cost estimates. For example, with customer demand, computing power increases, which raises software costs and developer dependence. SDLC provides a way to measure and improve the development process by providing insights and analyzing each stage, maximizing efficiency and reducing costs. How does SDLC work? The  
Software Development Life Cycle provides the guidance required to create a software application. It does this by splitting these tasks into phases that form the Software Development Lifecycle. Standardizing the tasks within each phase increases the efficiency of the development process. Each phase divides into granular tasks that can be measured and tracked. This introduces the capability of monitoring to ensure projects stay on track. The aim of SDLC is to establish repeatable processes and predictable outcomes from which future projects can benefit. SDLC phases are usually divided into 6-8 phases. The set of phases are: 
- **Planning**: The planning phase encompasses all aspects of project and product management. This includes resource allocation, project scheduling, cost estimation etc. 
- **Requirements Definition**: is considered part of planning to determine what the application is supposed to do and its requirements. For example, a social media application would require the ability to connect with a friend. 
- **Design & Prototyping**: establishing how the software application will work, programming language, methods to communicate with each other, architecture etc.
- **Software Development**: entails building the program, writing code and documentation. 
- **Testing**: In this phase, we ensure components work and can interact with each other. For example, each function works correctly, different parts of the application work seamlessly together, and performance-wise, there are no lags in processing etc. 
- **Deployment**: in this stage, the application or project is made available to users. 
- **Operations & Maintenance**: this is where engineers respond to issues in the application or bugs and flaws reported by users and sometimes plan additional features in future releases.

Companies can choose to rearrange by splitting or unifying these into 6-8 phases. For example, we can merge the testing phase with the Development phase in scenarios where security is introduced in every development step, as developers fix bugs during testing. It can depend on the Software Development Model; software development has evolved, as seen in the Intro To DevSecOps room. SDLC models include Waterfall, Agile, and DevOps, amongst others.  
### Questions  
  
*How many phases can an SDLC have? (Format X-Y)*  
  
>[!question]- **Answer**  
>  6-8
## SDLC Phases Part 1  
---  
### Information  
﻿The first phases focus on breaking down the project or application before moving on to the development of the application.
﻿1. Planning
	﻿1. As part of the Planning Phase, also known as the Feasibility Stage, the scope and purpose of the application are determined. Software development is planned and implemented using it. Additionally, it helps to keep the project focused on its original purpose while setting boundaries. Here, the system's problem and scope are defined, and the requirements for its upcoming design can be determined. The process of devising an effective outline for the forthcoming development cycle should enable issues to be caught before they have a detrimental effect on the process. And help them identify the resources they need to make their plan happen. The planning stage can be crucial if the goal is to have a product ready for market by a specific date.
﻿2. Requirements Definition
	﻿1. A system's requirements stage involves defining the prototype ideas and gathering all the necessary details. This may be in the form of: Making a list of all the requirements for the prototype system Prototypes should be evaluated for alternatives Identify the end user's needs through research and analysis Planning for the application involves defining the requirements to determine what it should do, and its needs. An application that uses social media, for example, will require you to connect with a friend or in some inventory programs, there is a search feature. Defining the resources needed to build the project according to the requirements is also critical. For example, software might be developed to control a custom manufacturing machine. A device is required for the process. It is common for developers to produce a document known as a software requirement specification (SRS)
﻿3. Design and Prototyping 
	﻿It is first necessary for developers to outline the details of the overall application, including its attributes, such as: 
		﻿1. Interfaces for users 
		﻿2. Interfaces between systems 
		﻿3. Requirements for networks 
		﻿4. Instances of databases 
	  SRS documents are usually converted into logical structures implemented in programming languages. Plans for operating, training, and maintaining the system will be drawn up to ensure developers know what they need to do throughout the life cycle. Here are a few examples: An architecture specifies how codes are written, industry practices, the overall design and any templates or boilerplates used within the program. Input is received and processed by the software through the user interface, which defines how the software interacts with customers. Defining a platform means choosing which media will run the software. It is not only about programming languages but also about solving problems and performing tasks in an application. A communication method specifies how an application communicates with other assets, such as a central server or other instances of the application. Application security measures may include SSL traffic encryption, password protection, and secure user credentials storage. 
	  
	  A document called an Architecture Design Review (ARD) is typically created by engineers and developers at this stage to ensure that all teams working in different areas are on the same page. In the case of an API endpoint, for example, front-end and back-end developers and teams handling authentication and authorization will be involved in the ARD process.
﻿1.  Software Development 
	﻿1. Code is written, and an application is developed based on specifications outlined in earlier design documents. Software developers appreciate instructions and explanations. Playbooks and guides for the application can be documented as part of the documentation process. Developers will use compilers, debuggers, and interpreters to adhere to coding guidelines established by the organization. A very effective initiative to promote secure coding would be incorporating code hygiene, code best practices and security in playbooks.  
### Questions  
  
*What phase focuses on determining the first idea for a prototype?*  
  
>[!question]- **Answer**  
>  requirements definition
  
*What stage is also known as the "Feasibility Stage"?*  
  
>[!question]- **Answer**  
>  planning stage
  
*When do you outline the user interfaces and network requirements?*  
  
>[!question]- **Answer**  
>  design and prototyping
## SDLC Phases Part 2  
---  
### Information  
The final phases focus on testing the application before release and maintaining its healthy operability afterwards.
5. Testing  
﻿It's critical to test an application before making it available to users. During the testing stage, developers will review their software using automated tooling, like source code scanners. The project's goal is to meet the previously defined quality standards during the planning and requirement stages. Testing is an essential pillar in moving toward a more Secure Development Lifecycle. To introduce testing effectively in the SDLC, it has to go through its own "Software Testing Lifecycle" phases. Sometimes, there are dedicated teams as part of a testing function. For example, a Quality Team with Quality Analysis (QA) Engineers. The most notable phases when introducing testing are test case design and development, test environment set up and test execution.
﻿**Test case design and development**
﻿With the test plan in place, testers can begin writing and creating detailed test cases. In this phase, the QA team fleshes out the details of the structured tests they will run, ensuring that it meets the requirements set in the previous SDLC phases. When conceptualizing test cases, the tester's goal should be to validate functionality within the allotted time and scope, especially core functionality. Test cases should be simple, well understood by any team member, and unique from other test cases. Test cases must be identifiable and repeatable, as developers will add new functionality to the product over time, requiring tests to run again. They can't change the test environment for future tests, especially when validating configurations. Test cases might also require maintenance or updates over time to validate both new and existing functionality. Once test cases are ready, a test team lead or peer can review them or check and update automated test scripts. 
﻿**Test environment setup**
﻿The test environment provides the setting where the actual testing occurs. Testers must access bug reporting capabilities and the application architecture to support the product. Once ready, testers establish the test environment's parameters, including the hardware, software, test data, frameworks, configurations and network. For example, most of a product's users might be on an Android device, use a specific version of a Chrome browser and have a certain amount of processing power on those devices. These are parameters the test environment would include. 
﻿**Test execution**
﻿At this stage, testers execute all test cases. For example, QA engineers and automated scripts run several functional and non-functional tests. Testers will identify and report detailed bugs from test case execution and log the system's performance compared to its requirements. Often testers retest the product, as part of regression testing, as developers make fixes to ensure new flaws don't get into production. With all of these tests piling up in the test execution phase, it's essential to use test automation to achieve the test coverage and velocity you need. Developer velocity is a metric that helps us understand and estimate how much development our team can perform in a given timeframe. 
﻿6. **Deployment**
﻿After testing, the overall design for the software starts to come together, and different modules or configurations are integrated into the primary source code. After this stage, the software is  
DevSecOps pathway. These tools focus on what you call "Software Deployment tools" for release management; the focus is on automating software rollouts so that teams can deploy new applications on all machines or just selected ones. This is particularly important if the new package requires actions to deploy correctly (a reboot of the machine, for example). Popular Software Deployment tools are Netlify and Argo CD. During the deployment phase, a new feature on the company's website can  
 be released, or in the case of mobile development, download a new application version on a. Furthermore, automating the deployment processes also allows the capability to rollback a deployment, making it easier to go back if there are any unforeseen circumstances with the deployment.  
7. **Operations and Maintenance**  
Developers must now move into maintenance mode and begin practicing any activities required to handle issues reported by end-users. Furthermore, developers are responsible for implementing changes the software might need after deployment. In this phase, users discover bugs they didn't find during testing. For example, handling residual bugs that could not be patched before launch or resolving new issues raised during user reports.﻿ Developers now focus more on stability and uptime than developer velocity, and operations teams now have a stake in developer velocity and their traditional role of maintaining uptime. When it comes to the specific part of operations in DevOps, this often means:
- They enable self-service for developers to promote developer velocity, where developers seek their solutions. Operations teams work closely with developers to provide on-demand access to secure, compliant tooling and environments.
- They standardize tooling and processes across the business. The best way to enable a sustainable self-service model and empower teams to work autonomously is by standardizing tooling. Tools and techniques that are standardized and well documented enable organizational unity and greater collaboration. This reduces the friction developers and operations teams experience when sharing responsibilities. 
- They are bringing extensible automation to traditional operations tasks. DevOps teams focus on empowering other teams through self-service and collaboration. Standard operations tasks like resolving incidents, updating systems, or scaling infrastructure still need to be addressed. When development and DevOps work closely together, teams automate the repeatable tasks and drive consistency across the organization. DevOps teams can track and monitor metrics thanks to consistency and automation of tasks. For example, by automating the creation of virtual machines in the cloud through Terraform, you can log activity for virtual machines created and accessed. You can extend this further by creating alerts for how the service accounts/roles are used to develop infrastructure from a security and compliance point of view. As operations teams shift towards greater automation, 'X' as code becomes the new normal. As example of this would be Vagrant or Ansible. The code controlling operations systems must be stored, versioned, secured, and maintained.  
### Questions  
  
*What phase focuses on handling issues or bugs reported by end-users?*  
  
>[!question]- **Answer**  
>  operations and maintenance
  
*What phase involves releasing new versions of software?*  
  
>[!question]- **Answer**  
> deployment 
  
*What phase ensures software meets the standards defined in the requirements phase?*  
  
>[!question]- **Answer**  
> testing 
## Keep CALMS  
---  
### Information  
﻿[CALMS](https://www.atlassian.com/devops/frameworks/calms-framework), as explained in the Atlassian post, is a framework that assesses a company's ability to adopt DevOps processes. The acronym was coined by Jez Humble, co-author of "The DevOps Handbook," which stands for Culture, Automation, Lean, Measurement, and Sharing.
﻿Culture 
﻿As highlighted in the Intro To DevSecOps room, DevOps isn't simply a process or a different approach to development; it's a culture change. For any DevOps adoption to be successful, an organisation will have to make a culture shift. Rather than the slower, full-release approach of the waterfall model, teams will have to adopt new strategies to break projects into smaller tasks that can be completed and then presented in a series of sprints. This culture shift is required for all employees, including not only the development teams but also QA, product management, and operations.Automation﻿A large part of DevOps is the focus on automation. Since we are breaking projects into smaller components, it would be inefficient to then manually integrate these components into the final solution. Thus, it is better to spend some time creating automated processes that can ensure that new feature integrations can occur in a reliable and repeatable manner. This is usually started on the continuous delivery side of things for new teams. But as teams mature, it will also move to continuous integration.Mature teams can also look to automate the configuration itself through tools such as configuration as code. This means that the configuration of the application itself is defined in code, which would alter build instructions depending on the environment that the application is being built for. This streamlines the process of building production-ready code, and configuration parameters could be used to reduce the verbosity of errors and remove developer bypasses before the code is built for the production environment.LeanBy implementing DevOps, we want to make sure that tasks are broken as small as possible. This allows teams to create initial versions of applications sooner. The common principle is that we are constantly improving our software, but it is more valuable to get a version of our application in the hands of users earlier rather than having to wait years until the product is fully perfected. Thus, we start with a lean first version that is constantly improved with time. This method also allows our user base to provide feedback and a wishlist of features for the application. MeasurementWhen implementing DevOps, it is important to have some sort of measure of effectiveness. These metrics are important since they will help us make small changes to our processes and ensure that we are constantly improving. In the next task, we will elaborate on how DevOps handles measurement and essential metrics to seek constant improvement and monitoring.SharingIn an effective DevOps pipeline, there is a shared responsibility for the overall application between all teams, including development and operations. Understanding that all team members are required to deliver the final solution and share in the responsibility to do so will result in a better product for users.  
### Questions  
  
*What does CALMS stand for?*  
  
>[!question]- **Answer**  
>  culture,automation,lean,measurement,sharing
## DevOps Metrics  
---  
### Information  
﻿It is crucial to understand what metrics DevOps engineers gather before you can advise and introduce security. As seen in the [Introduction to DevSecOps](https://tryhackme.com/jr/introductiontodevsecops) room, gaining common ground to build perspective and empathy is crucial for buy-in and instilling security.
﻿
#### DevOps Metrics
﻿﻿During the process of manually creating infrastructure, deployments are blocked. There may be too many errors in the live application, indicating that the security test automation needs to be improved or is taking too much computing power and time. Understanding how and where to find improvement requires metrics to measure your resources. Here are the essential metrics gathered by engineers and the questions it aims to answer:
﻿- Meantime to production ([MTTP](https://about.gitlab.com/handbook/engineering/infrastructure/team/delivery/metrics.html)). What is the turnaround time for newly committed source code?
﻿- Frequency of deployment. What is the frequency of deployment of releases? The average lead time. How long does it take to develop, build, test, and deploy a new feature?
﻿- Speed of deployment. A new release is deployed into production; how long does it take?
﻿- Deployment Agility. You can measure deployment agility by combining deployment speed and frequency.
﻿- Production failure rate. How often do failures occur in production?
﻿- MTTR stands for mean time to recover. What is the recovery time after a failure?
#### ﻿MTTP
﻿One critical DevOps metric to track is the mean time production. MTTP is the length of time between when a code change is committed and when it is in a deployed state. A pre-release test, for instance, is passed when all code requirements have been met. Test automation and working in small batches are good ways to improve MTTP time. Developers can receive fast feedback on the code they commit by following these practices, identifying flaws, and fixing them as quickly as possible.  
#### Failure Rate
﻿ When a code change goes into production, a certain percentage of code changes require hot fixes or other remediation measures. It does not measure failures caught during testing and fixes before the code is deployed. The same practices that enable shorter MTTP times correlate with reducing change failure rates. All these practices make bugs much easier to identify and remediate. Tracking and reporting failure rates are essential for ensuring new code releases meet security requirements.
#### Deployment frequency
﻿ Understanding how often new code is deployed into production is critical to DevOps' success. Deployment frequency defers to MTTP as it measures when it's released into a pre-production staging environment and reserves "deployment" to refer to code changes released into production. Teams can deploy changes on-demand and often many times a day. The ability to deploy on-demand requires a deployment pipeline that incorporates automated testing and feedback mechanisms, as mentioned in the previous tasks, minimizing the need for human intervention. 
#### MTTR
﻿ When a partial or total service interruption occurs, the mean time to recovery (MTTR) is measured. Keeping track of this metric is crucial. If a failure occurs, a fix must be deployed as soon as possible, or the changes that caused the failure must be rolled back. In most cases, this involves monitoring system health continuously and alerting operations in the event of a failure. The operations team have the necessary processes, tools, and permissions to resolve incidents. 
#### Communicating Risk
﻿ You can demonstrate improvement over time by measuring any of these, and you'll have the evidence to support the buy-in from the business and teams. Risk means very different across teams. For DevSecOps engineers, risk means the likelihood of a vulnerability being exploited and its impact on systems. Whereas for a DevOps engineer, a significant risk would be high rates of production failure, for example. By understanding other teams' definitions of risk, a DevSecOps engineer can find common ground and better build a perception of security risk for other teams.  
### Questions  
  
*What 2 metrics are used to measure deployment agility?*  
  
>[!question]- **Answer**  
>  deployment speed and frequency
  
*What is an essential rate for engineers in Production environments to know if code meets security requirements?*  
  
>[!question]- **Answer**  
>  failure rate
  
*What is the measurement for recovery time after a failure?*  
  
>[!question]- **Answer**  
>  mttr
## Production of the Droids  
---  
### Information  
﻿﻿**The Empire Expects Great SDLC**
Now that we understand SDLC principles, it is time to put them to the test! Launch the static site attached to this task. You have been placed in control of a droid production factory!The empire has provided you with a round of seed funding of $1,000,000. However, the empire expects a great return of double the initial investment! Using these funds, you are tasked with hiring developers and deciding how many sprints these developers will have to build droids. For this task phase, it is important to remember the Mythical Man Month principle (also called Brooks's law) that states: "Adding human resources to a late software project will make it later". So be careful, as adding more developers might decrease the efficacy of your sprints!
Once you have decided on the number of developers and sprints, it is time to allocate these sprints to the various SDLC phases. As you add sprints, pay careful attention to how this will affect your factory's effectiveness. Once you believe you have found the optimal split of sprints, there is nothing left to do but start the production machine! 
While the challenge is to double the investment, with some smart thinking, you should be able to achieve quite a bit more than that! Think you have achieved a high score? Share it with us on the Discord channel and LinkedIn!  
### Questions  
  
*What is the flag that you receive once you have doubled the empire's investment?*  
  
>[!question]- **Answer**  
>THM{Ruler.of.the.SDLC.Droids}