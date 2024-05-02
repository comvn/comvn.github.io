---
layout:     post
title:      Scaling Up
subtitle:   Best Practices for Mobile Development Teams, Architecture and Workflows
author:     NDA
header-img: img/posts/coder01.jpeg
header-mask: 0.5
catalog: true
tags:
    - Development
---
![]()

# Introduction

Users and developers alike ask a lot of modern mobile apps. They have to be fast, reliable, functional, packed with features, and regularly updated. Creating apps that meet each of these requirements is a task for developers that increases in difficulty as the user base and feature set grow. Success brings its own challenges, whether app traffic rises steadily or surges vitally. The app team and architecture must be ready to handle more—more users, more sessions, more crashes, more reviews, and more pressure to make every impression count.

Just as your team should be setting performance standards as you grow your app capabilities, you should also implement good practices for your app’s team structure and architecture as you scale. The principles of scalability have a lot in common with sustainability—scaling apps require developers to reduce, reuse, recycle, plan carefully, and think outside the box. Solid mobile app architecture built with strong standards will deliver flexible, dynamic apps that can handle the traffic and grow with their user base.

By incorporating clearly defined app architecture and development practices from the beginning stages of your app’s development, you proactively build in support for future growth, flexibility, and reliability that will make your continued scaling efficient and manageable. Effective scalable architecture, tools, teams, and workflows all contribute to better app performance, which translates directly to revenue growth—about 50% of consumers will spend more with a company if its digital services are better than those of a competitor. Reaching that superior performance means preparing for growth before it outpaces your app’s capabilities.

Future-proofing your app means making architecture, tool, and workflow choices that enable your app to grow sustainably and evolve with your needs. In this ebook, we’ll discuss principles of scalable mobile app architecture and performance optimization at scale, and explore Instabug’s role in helping your teams efficiently manage app quality and performance at every stage of growth.


# Creating Efficient Engineering Teams

Bugs and crashes are an inevitable part of the development process, but scaling apps and teams face unique challenges when it comes to handling quality fixes. The sheer density of information crash reporting software collects can become overwhelming for teams to manage at scale—in fact, some of the most pervasive time sinks for large engineering teams are unrelated to coding.

Often, organizational issues are as much to blame for these time and effort costs as technical hurdles. The quantity and diversity of incoming crashes increase with application size and complexity. These factors increase the time and personnel needed for issue discovery, triaging, and assignment, slowing overall issue resolution time.

For companies with large mobile engineering teams, building efficient team structures and crash workflows is a crucial, proactive move that will reduce issue resolution time. So, how do quality-oriented engineering teams at scale optimize efficiency while prioritizing performance? In this section, we’ll explore common challenges large engineering teams face and strategies for solving them.

‍

## Challenges for large teams
‍

**Team structure**: Large applications have many components and features, each one adding complexity in coding and performance management. Operations like payments, orders, Know Your Customer verification and compliance, etc., add layers to the development process, necessitating division into subteams. Typically, each subteam is responsible for a different part of the code. This division often comes at the cost of reduced visibility and collaboration between team members, and potential for engineers to step on each other’s toes, so to speak. If responsibilities aren’t clearly defined and divided between teams, it can lead to feature creep, code conflict, or confusion and delay during crash assignment and resolution.

**Triaging fixes**: Releases inevitably involve bugs and crashes, and scaling apps have even more to manage. But not all errors are equal—developers have to determine which issues are not worth fixing and deploy fixes where they are most impactful. It can be difficult for both leadership and engineers to identify the most critical performance and stability issues to tackle with urgency. Knowing which issues to prioritize is imperative for keeping teams on schedule and user satisfaction rates high.

**Issue assignment**: When applications scale and crashes increase in density and origin, it takes longer for teams to assign them to their proper owners. Manually assigning crashes becomes overwhelming with application size, so much so that large enterprises often hire product managers for the sole purpose of assigning incoming issues. They need to be able to determine where the crash originated and which team member to assign it to, a process that consumes valuable time.

**Release cycles**: With the introduction of each new feature, coupling introduces code conflicts and decelerates development cycles. Build times typically escalate as teams and apps grow larger. These longer release cycles affect issue resolution time, user satisfaction, and even user acquisition rates. The top-grossing apps typically update once every two weeks. The more dependencies within both your app and team structure, the longer it will take to orchestrate releases.

**Error detection and debugging complexity**: With large apps, it’s natural for numerous quality issues to exist, and addressing those issues requires an abundance of data. In order to detect all issues and collect enough information to debug them, app performance must be comprehensively and continuously monitored. This task goes from increasingly difficult to impossible to manage with legacy performance monitoring software as applications grow. Many tools are incapable of even detecting critical issues such as UI hangs, which are extremely disruptive to the user experience. Developers need an abundance of data–and the right kind of data–to debug efficiently. Finding patterns in large sets of data is a time-consuming task that the right performance monitoring software can expedite.

‍

## Best practices for team efficiency
‍

**Organization by ownership**: An efficient way to organize large teams is to divide members based on the features or modules within your app(s). Establish clear team ownership rules for each member’s respective parts of the code, so that everyone knows exactly which bugs and crashes belong to them. You could delineate these teams by feature and app, or, if you have multiple apps with shared architecture, across multiple apps. Clear division of responsibilities will reduce confusion and make crash assignment straightforward.

**Internal consistency**: Create shared processes across teams. For example, establish company-wide templates for planning and design documents. Standardize naming conventions and language between apps and teams for concepts such as features, spans, flows, and file names. Consistency will make it easier to categorize, address, and assign issues as they arise.

**Shared architecture**: If your organization is responsible for multiple apps, consider reusing architecture during development of new features and apps. This will eliminate redundancies when developing similar features across multiple apps and make common issues easier to assign and debug. For large quality teams, you can divide teams based on function, such as feature flags, experiments, or specific performance metrics, rather than creating app-specific teams.

**Team collaboration**: Foster an environment of collaboration between and within teams by implementing cross-team and cross-platform planning sessions and syncs. Meeting regularly will help teams avoid feature creep and overlapping or overlooked responsibilities. In addition, regular interaction builds stronger team communication, especially among dispersed or remote teams.

**Peer code review**: Regularly review your code base as a team to share challenges and solutions. This practice will also help with onboarding new members and standardizing during development. Peer code review not only improves communication within your team, but connects a larger web of expertise, resulting in a better overall app. Additionally, it can help developers detect and fix issues rapidly, costing less money and effort in the process.

**Mobile-first solutions**: Mobile apps require the sensitivity of mobile-first solutions to detect and debug all quality issues. Many crashes and errors that cause crash-like behavior—issues like app hangs, ANR and OOM errors—go undetected by other platforms. NDK and C++ crashes are invisible to most crash reporters, yet have the same negative impact on the user experience. Full visibility into these issues will save your team from addressing them late or missing them entirely.

**Tools and team integration**: The software your teams use in development will shape their everyday experience and overall workflow efficiency. For example, crash reporting solutions need the flexibility to recognize team and code divisions. Crash management gets noisy; being able to calibrate team dashboards keeps members focused on what’s relevant to them. Moreover, your crash reporter should also have a diversity of integrations to accommodate the other tools you already use so your team avoids building workflows around inflexible solutions.

**Workflow automation**: The fastest way to improve your team’s issue response and resolution time is to automate as much of the quality process as possible. With the right information, you can triage and assign tasks without human intervention. For example, using Instabug, you can set rules that automate assignments and alerts for incoming crashes or performance events. By removing the time and effort spent manually identifying, triaging, and assigning issues, your teams can focus their efforts on what’s important to them—and ship fixes faster.


# Building Scalable App Architecture

## Characteristics of scalability
‍

![](https://assets-global.website-files.com/6270e8022b05abb840d27d6f/64071d5af2a5add938536d69_Characterstics-01%401x.png)
‍

What does it mean for an app to be scalable? From an architecture perspective, it means an app is able to grow its user base by two or more times the current traffic and still efficiently handle the workload without sacrificing performance quality, and without taking expensive measures to do so. For apps with well-designed architecture, increased traffic or computational demands won’t cause failures or slower performance.

There is no one way to design a scalable app architecture, but successful scalable projects have a few characteristics in common: they are designed for flexibility, stability, and ease of updates. Developers can make changes without impacting entire frameworks or proliferating errors. Resource usage is optimized for both cost and computational efficiency. The app’s performance remains fast and stable even as workloads grow. As your app increases in size, functionality, and features, thoughtfully designed architecture will resolve otherwise complicated issues by making the problems easier to understand, easier to test, and easier to change. Ultimately, architecture serves as the foundation of a well-designed, highly functioning mobile app that offers stable performance and a great user experience.

Development teams can avoid common issues scaling apps face, such as strained servers, climbing maintenance costs, and falling user satisfaction scores, by establishing sustainable design principles and standards early on in the build.

‍

## Creating cohesive systems
‍

![](https://assets-global.website-files.com/6270e8022b05abb840d27d6f/63e50e2e904054ee8e959996_Asset%201%404x.png)
‍

**Optimize software and code to use fewer resources with more capabilities—but your work doesn’t stop there**. In addition to code that scales with you, your backend infrastructure will also need to accommodate growth. Some app owners outsource this challenge altogether by using a Backend-as-a-Service (BaaS) provider. For those who build custom, there are two main strategies for infrastructure scaling—scaling up and scaling out, which we’ll discuss briefly (more on infrastructure scaling for mobile apps).

Vertical scaling, or scaling up, maximizes capacity from individual servers by adding more memory or processing power to each instance. This strategy has a limit, though; a single server can scale a lot, but not forever. Horizontal scaling, or scaling out, however, can be virtually unlimited depending on resource availability because it increases a cluster’s capacity with additional servers. Using load balancing, horizontal scaling distributes requests more evenly across all machines, including the added servers, to prevent overloading. A hybrid approach, diagonal scaling—scaling up and out—mixes the two strategies and requires dividing the project into agile modules to keep the various aspects of the app flexible.

‍
![](https://assets-global.website-files.com/6270e8022b05abb840d27d6f/63e286a6827180b39ea249e7_Asset%202%402x.png)

‍

Developers need team designations and workflows that can scale with them as well. Without scaling up their human processes congruently, teams may experience strain due to an influx of issues with too few resources to handle them. Even the best-designed systems need to optimize every human touchpoint for maximum efficiency. Time-consuming manual workflows can quickly become bottlenecks; inefficient triage and assignment of bugs and crashes can lead to gaps in addressing critical issues if they fall through the cracks unflagged.

One of the main goals of designing scalable systems is achieving better performance. For front-end performance at its best, you need the right software to fully analyze your app under all conditions and for every user interaction. Measuring app launch, UI responsiveness, and loading times will help you understand how well your components are working together and where inefficiencies are causing congestion. Variables like low battery state or poor network quality can cause user-specific deviations in performance. By using Instabug, you’ll be able to detect and monitor all of those issues. Accurate issue discovery, transaction metrics, and robust analytics will help you make targeted improvements to your app’s performance.


# Scalable Design: Principles of Sustainability

![](https://assets-global.website-files.com/6270e8022b05abb840d27d6f/63ecdd61ea1e566214035e08_Asset%202%404x.png)

Software architects and urban architects share many considerations when planning projects. When planning a new project or renovation, these architects must balance the needs and wants of the client, how to work with the site’s landscape and surrounding conditions, and how best to make use of existing resources. No client comes with an infinite budget, and there are always other limitations—legal and structural requirements, future maintenance needs, the laws of physics, the site orientation and local climate.

App developers are bound by similar types of requirements, albeit through a different media. Like architects, developers cannot design in a vacuum. They must consider how components will interact with each other, how they can be changed later, and what kind of maintenance they’ll need. The software must also consume limited resources, meet performance standards, and adhere to legal requirements for data usage and privacy. Long-term, scalable app architecture design requires holistic thinking with consideration for efficiency, functionality, longevity, and future needs.

Working in a world with limited resources, cost consciousness, and the expectation of growth means that architects and developers should follow the same general principles of sustainability—reduce, reuse, and recycle, with careful curation of new additions. There must be a harmonious balance between what’s built, what’s bought or spent, and the overall end-user experience. Let’s explore how these ideas translate to scalable mobile app development.

‍

## Reduce
‍

Dependencies: Reducing dependencies is a guiding principle for developers planning to scale. This approach alone can significantly improve both app speed and overall stability. Dependencies between classes, services, and third-party software often cause crashes, failures, and slow loading times. For example, it’s common in mobile apps to decouple the business layer from the presentation layer so that loading the UI won’t drag due to tasks like data verification. In addition, the fewer interlinked processes and components in your app, the easier it is to make future changes without affecting existing code. The more you can decouple new updates from your old code, the easier it is to continue updating and improving your app, while more seamlessly growing your team and functionality.

**Third-party tools**: External libraries and frameworks come with a cost—the more third-party dependencies and frameworks your app relies on, the more performance slows, the time it takes to patch updates increases, and the risk for errors with updates multiplies. Poorly optimized or buggy software development kits can block critical processes and delay loading. Third-party inclusions also increase overall package size, so it’s important to make sure they’re worth the weight. If you’re using only a small part of a third-party framework, consider removing it altogether and replacing it with in-house assets to perform the desired function. The third-party tools that make the final cut should consume minimal resources and perform functions considered essential.

Performance monitoring and management, for example, are indispensable for modern apps and can help you make informed decisions about next steps in development. Use of CPU, memory, and mobile wait times are a few metrics that will help you track how large you need to scale by unveiling where your app is slowing due to traffic bottlenecks. Third-party tool selection also impacts workflow efficiency, both in software and team processes. Tools you consider should integrate with software you already use, so you don’t have to overhaul your workflow whenever something changes. Choose tools carefully, taking time to consider how your needs may change in the future and how you'll be able to accommodate those changes. You should also be able to decouple tools from dependencies without impacting the whole app architecture.

There is no “one-size-fits-all” solution when it comes to choosing the right tools for your app architecture. Some will perform well throughout a longer lifecycle, while others will only be appropriate for small or large-scale apps—not both. Ideally, the tools you select should help you get the job done quickly and successfully at your current stage of growth, with room to evolve or upgrade later. For the critical function of performance monitoring and management, Instabug is a solution that can grow with your app from your first beta to millions of users.

**Heavy activity initialization**: Activity creation can be resource intensive and may generate bottlenecks. Avoid delays and network congestion by moving blocking work off the main thread and sending it to background threads to be performed asynchronously. You might defer refreshing homepage data, for instance, until after the app loads the rest of the page elements. You can also reduce your memory usage and workload by caching resources and computations when possible. Optimizing your memory and CPU usage will shorten loading and wait times.

**Dynamic libraries**: Identify specific processes or tools you can simplify. Many dependencies added as dynamic libraries will increase loading times, so wherever possible, change frameworks to static libraries. Dynamic libraries are loaded at runtime, while static libraries are loaded at compile time. If a static library isn’t an option, reduce load times by resolving libraries asynchronously with a prelinking tool.

‍

## Reuse
‍

**Development processes**: For developers creating growing apps, organizational efficiency starts with shared processes and resources. Standardization helps large teams streamline development and quality management processes, even if the team or app is separated into distinct modules. For example, shared design documents, naming conventions, and workflows contribute consistent methodology that teams can maintain even as features or staff change. By unifying language used for spans, screens, and modules, all developers and new team members can quickly understand the base code and easily target and assign issues with automation. Teams can also conduct regular code reviews to share challenges and solutions, help with onboarding new members, and encourage standardization during development.

![](https://assets-global.website-files.com/6270e8022b05abb840d27d6f/63e2875f849fe33eef7a8ac1_Asset%206%402x.png)

**Code reusability**: Code reusability is the ability to repurpose pre-existing code for new software applications. The repurposed code should be stable, functional, and easy to implement. Reuse must be thoughtful—It’s crucial to ensure that the code you’re reusing is appropriate for its new purpose. Make this easier from the start by keeping code flexibility and reuse in mind when your team begins planning your architecture. From a performance perspective, when code has worked well in one area, it’s less likely to cause problems or breaks in other areas. From a size perspective, the more code you reuse, the smaller the package size.

**Shared architecture**: When an organization owns many apps, shared architecture can increase efficiency on many levels. For instance, reusing code between apps eliminates redundant research and development efforts when developing related features. Sharing and reusing code also makes it easier to assign and debug common issues in a methodical way. Use shared architecture across apps to automate or simplify tasks like crash assignment and debugging, streamline fixes, and improve efficiency at the organizational as well as the team level.

**Caches**: Save your app from repeating computationally intensive tasks by caching. By reusing previously fetched content, you can reduce both latency and processing demands. Reading data from memory takes milliseconds versus actual seconds for disk processes or requests that pass through multiple network layers. Caching also eliminates the costs associated with performing the same work multiple times, which can be significant, especially when manipulating scaling databases. Content delivery networks (CDNs) also speed up retrieval of content by delivering regionally cached assets. Ultimately, both of these content strategies will improve the user experience by cutting down on load times, which should be two seconds or less to avoid user abandonment.

**Performance tests**: Write robust tests, and use those tests again, again…and again. Obsessive testing in beta can save developers from bugs in production, which cost exponentially more to fix as an app scales. Test everything, from the quality of the code itself to the flexibility, scalability, and stability of your architecture. Load testing reveals performance bottlenecks in extreme traffic conditions. Device hardware specifications and battery states can also trigger anomalies. For your tests to be effective, your app needs the sensitivity of mobile-first performance monitoring software, which captures and reports everything from cumulative metrics to full breakdowns of individual transactions and device states.

‍

## Recycle
‍

**Solutions**: It’s often said, “If it’s not broken, don’t fix it,” but the adage doesn’t always hold true in mobile app development—there’s almost always room to iterate and improve on what you’ve already built. Use performance monitoring software to identify areas where you can tweak solutions or rework them for better results. You can apply his approach to more than just metrics—you can recycle and refine existing ideas, structures, and processes, too. In software, nothing lasts forever. “Does it work?” is no longer the bar for conversions thanks to the competitive nature of mobile app marketplaces. Instead, how well and how fast it works are moving goalposts that require ongoing effort to maintain progress and competitive advantage.

**Frameworks**: Your app architecture should be fairly easy to change without introducing errors or negatively impacting existing elements. Ensure a smooth process by embracing modularity: use modules that you can swap out individually rather than updating multiple components. Separating modules also prevents code issues from impacting the entire app so your team can isolate and resolve performance issues faster.

**Experiments**: Test, iterate, and tweak existing experiments. What have you learned from previous experiments, and where else can you use this information? Don’t make assumptions about user preferences and habits; test your features—and biases—frequently under an array of conditions. To improve app stability, use feature flags. The ability to turn modules on or off in the event of code conflict and bugs or crashes will help your team prevent issues from spreading before it can isolate and resolve them. Instabug recognizes feature flags and can report on app performance related to your experiments.

**Problem**: In addition to reworking old solutions, prepare for the future by considering alternative ways to solve the same problems. Even though mobile devices are always evolving, their users will still have many of the same needs. Therefore, there will be opportunities to capitalize on finding new ways to solve old problems, using advances in technology like voice and language processing, new mobile hardware features, and more. Requirements around existing solutions may also evolve; for example, apps modify or remove some third-party services to comply with GDPR requirements regarding the collection or sharing of data. Revisit old challenges, look for alternative solutions, and consider future constraints—your teams, ideas, and code must all be flexible to adapt and rule the marketplace.


# Managing Performance at Scale

Scalability encompasses more than just code—not every workflow or team structure allows for efficiency at scale, creating issues for app users as well as developers. If teams and tools can’t adapt to numerous and complex maintenance tasks, triaging and assigning quality issues can become bottlenecks for release deadlines and overall app performance. For large teams to maintain productivity and efficiency at scale, their tools and workflows need to be able to scale with them.

The top-grossing apps release updates about once every two weeks, but well-designed development pipelines can ship more often without breaking things—mega apps like Facebook can deploy updates multiple times weekly or even daily. Your optimal release schedule depends on your team and resources, goals for releases, and the quality of your internal testing regimen.

At Instabug, we use a combination of productivity tools and a performance-first DevOps mentality to facilitate timely, stable releases. Task automation enables our teams to work smarter, not harder—supporting a focus on innovation rather than repetition. In this section, we’ll outline some of the tools and strategies we use to help divided teams achieve fast-paced, high-performance releases.

‍

## Large-scale DevOps and CI/CD
‍

DevOps is a combination of Development and Operations—two traditionally distinct disciplines—united into one pipeline encompassing the development, deployment, and monitoring of all app releases. This is done through collaboration between developers, project managers, and the operations team. DevOps enables efficient use of resources by shortening the time to release, improving code quality, and overcoming blockers quickly. By adopting DevOps strategies, developers can release high-quality code more easily and more quickly.

‍
![](https://assets-global.website-files.com/6270e8022b05abb840d27d6f/63e50e9b3de3de4ae970d6b5_Asset%202%404x.png)

‍

The DevOps pipeline is a looping cycle aided by continuous integration, delivery (CI/CD), and deployment. With CI, developers continuously commit new code to a version control repository. The newly submitted code is merged with the current code, creating a new build. The new build is tested automatically through CI tools, which identify and fix defects and bugs on the spot. Undergoing the same process manually can cost developers hours of additional work every week—adding days and even weeks to timelines for larger releases.

Combined with the continuous integration/continuous deployment (CI/CD) process, mobile DevOps can speed up the time to release by 20%. Between continuous integration and deployment, there’s the continuous delivery stage. Successful builds in the CI pipeline are delivered to a staging environment to test performance, security, and more. These are the final tests before the build progresses to a live environment.

Continuous delivery also serves as a buffer between integration and deployment. The QA team gets involved at this stage and to ensure the build is stable and meets performance requirements. The build from the continuous delivery pipeline is ready for deployment, but only released when approved. Continuous deployment automates the deployment process and takes the build from the staging environment to production.

‍

There are three aspects to successfully adopting Mobile DevOps:

* **Culture**: Moving from the conventional model of development to Mobile DevOps requires a shift in culture and processes at your organization. You can ensure a successful transition by establishing an onboarding program about the new initiative, slowly introducing the new processes and providing them with adequate training.
* **Training**: DevOps, CI/CD (Continuous Integration/Delivery) for Beginners is a good place to start with DevOps training. The course is designed for beginners used to the more conventional development life cycle. It introduces the concept of CI/CD and DevOps and builds the foundation for more advanced courses down the road.
* **Tools**: On top of the stack you already use, you’ll need Mobile DevOps platforms such as Bitrise or Codemagic. These platforms help automate manual processes and integrate with your current stack. You can switch to CI/CD processes with either of the platforms and use Instabug for continuous monitoring to complete your Mobile DevOps tech stack.
‍

## Workflow automation
‍

**Onboarding**: At Instabug, we incorporate automation into our development workflows as well as our team management. New members start with an automated onboarding process, which includes code review and familiarization. This approach ensures consistency in the content and quality of training received by each developer, as well as in their code. Keeping teams aligned with standardized processes and naming conventions allows for automating code maintenance task assignments during production.

**Testing**: Automation at Instabug also helps with testing code and staging development environments. We use an internal tool called Deployly, which integrates with GitHub repositories and creates automated testing environments. When a developer is ready to test their code, they add the PR link to their Deployly dashboard, and Deployly creates a new environment specific to the current branch. This allows developers to test code day to day without conflicting with existing environments.

**Deployment**: Tools and integrations automate several steps during our release cycles. A workflow creation tool helps us identify dependencies and automates the release deployment process. We also integrate Jenkins with our GitHub repositories, which perform automated tests and health checks. When all tests have passed and the code is merged to the master branch, Jenkins automates tasks that release the new code to production. We also integrate Jenkins with Slack to report whenever releases fail or go live.

**Releases**: Using release trains or a scheduled approach to release management helps set and maintain a release cadence. You ship new releases periodically, and anything that’s ready by the deadline gets released. With this approach, you don’t wait to ship full features, instead shipping limited parts until the feature is fully functional after a few releases. Using a scheduled, release-train approach for your mobile app is a best practice, especially if you’re managing a feature-heavy app. At Instabug, we have multiple teams concurrently releasing separate features, which means a lot of developers merging large amounts of code with the master branch. We created an internal Release Service Desk within Jira to handle this. Whenever a team wants to release a feature, they’ll submit a release request with all the relevant information. Our release train syncs with Google Calendar so that all teams know what’s been released or is scheduled to release at any given time. Automated Jira, Google Calendar, and Slack integrations keep our teams, schedules, and release notes aligned.

**Release monitoring**: After each release, you’ll want to monitor performance to see how the new code has impacted it—no test environment can perfectly predict every potential conflict once it hits the public. The larger and more complex your app, the harder it is to determine exactly which code or conditions contribute to slow processes, especially when they appear under certain conditions. System-wide observability enables you to pinpoint exactly where the problems lie, so you can begin targeting solutions. Instabug has a built-in release monitoring dashboard to give your team the adoption rate and vital metrics for every app version. Automated alerts and forwarding rules send real-time notifications to the proper team whenever a release triggers unsatisfactory performance. You can read more about release monitoring in detail in Mobile Release Best Practices.

**User feedback**: Feedback is an essential part of every release and any app’s continued growth, especially for teams that are planning to scale and invest in more features. Targeted feedback helps teams validate ideas, iterate and improve, and find out what isn’t working—and why. In addition to helping with product development, in-app feedback enables users to easily report problems without resorting to leaving negative app store reviews. In-app chat is also a valuable resource for managing user relationships. Using Instabug, developers can respond directly to questions, feedback, bug or crash reports and alert users of updates or fixes in progress. Feedback is another opportunity for automation—when app users reach the millions, managing replies manually is impractical. With Instabug, you can set rules for automatic replies based on specific criteria, so your users don’t have to wait.