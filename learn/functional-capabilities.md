# Functional Capabilities

_<mark style="color:blue;"></mark>_

<mark style="color:orange;">< Lead-in from Overview></mark>

### <mark style="color:orange;">**Key Capabilities that Sunbird Lern can enable:**</mark>

* <mark style="color:orange;">Launch Courses: Create and manage course batches, review user progress and performance on assessments, and issue rule-based certificate</mark>
* <mark style="color:orange;">User Engagement: Engage users through groups and discussion forums, events, and notifications.</mark>
* <mark style="color:orange;">User Account Creation & Administration Capabilities: New user account creation, user login/ authentication and user profile with passbook. Assigning and management of user roles. Management of location and other master data</mark>
* <mark style="color:orange;">Login & Authentication: Enable login via various methods including userID/ password as well as SSO via Google or similar systems</mark>
* <mark style="color:orange;">Notifications for users: Send notifications to users to inform them about programs deadlines or for system level activity such as generation of a certificate or creation of an account.</mark>

<mark style="color:green;">The following are the details of the functional capabilities that are enabled via Sunbird Lern:</mark>

*   <mark style="color:green;">Enable batches of students to take courses on the platform: Create and manage a course batch - that allows for a cohort of users to take the course within a specified time frame, review user course progress or assessment performance, issue rule based certificates for course completion, merit scores etc.</mark>&#x20;

    <mark style="color:green;">The</mark> <mark style="color:green;"></mark><mark style="color:green;">`Batch Service`</mark> <mark style="color:green;"></mark><mark style="color:green;">component of the Lern Building block is used to power these capabilities within Sunbird Lern.</mark>&#x20;

<mark style="color:green;"></mark>

*   <mark style="color:green;">Allow users on the platform to collaborate: Sunbird Lern components can be configured to give users on the platform collaboration capabilities. These components include the Groups Service as well as Discussion Forums. The functionalities enabled by the Groups component includes the ability for users to create a Group on the platform, add/ remove users from the group, as well as assign activities (content, assessments etc) for the users in the group to undertake. The Group creator is also able to track how much of the activities the users have completed. A Group can also have a Dicussion Forum attached to it, which allows a user to start or contribute to discussions on relevant topics. Such capabilities allow for users to learn together as a cohort, as well as engage in useful collaborative activities to further their learning.</mark>

    <mark style="color:green;">The components used to enable collaboration include</mark> <mark style="color:green;"></mark><mark style="color:green;">`Groups`</mark> <mark style="color:green;"></mark><mark style="color:green;">as well as</mark> <mark style="color:green;"></mark><mark style="color:green;">`Discussion Forum`</mark><mark style="color:green;">.</mark>

<mark style="color:green;"></mark>

* <mark style="color:green;">Enable users to create accounts to save their platform preferences, access relevant content basedon their preferences etc. Users with accounts on the system who login also get access to richer platform features such as Courses and Learner passbook. These capabilities are enabled using the</mark> <mark style="color:green;"></mark><mark style="color:green;">`User & Org Service`</mark> <mark style="color:green;"></mark><mark style="color:green;">component of Sunbird Lern</mark>



<mark style="color:green;"></mark>

* <mark style="color:green;">Platform administrators can be granted capabilities to manage user roles on the platform, as well as manage platform master data (eg. Location data, Framework values etc.)</mark>

<mark style="color:green;"></mark>

* <mark style="color:green;">Configure the platform to allow for user logins via various mechanisms including username/ password, Google login or single sign-on with other approved systems</mark>

<mark style="color:green;"></mark>

* &#x20;<mark style="color:green;">Configure the platform to be able to send notifications to users on events of choosing - these could be user driven or system driven events.</mark>

<mark style="color:green;"></mark>

_<mark style="color:blue;"></mark>_

A few sample use-cases where Sunbir Lern has been leveraged to effectively implement desired functionality include:

\> Integration of Sunbird to an existing system to allow valid `users` with accounts on the system to `login` via single sign-on to Sunbird

\> Bulk-create a set of user accounts for a set of `participants` in a workshop that `uses` an online platform/ Sunbird

\> Allow for `generation of and issuing of certificates` to `participants` of a course in a workshop that uses an online platform/ Sunbird

`> Assign rights` (say content creation rights) to an identified set of `users` for a content creation workshop

\> Assign a group of `learners` to a batch and allow them `take a course` within  specified start-end dates.

\> Enable a discussion forum for a Batch of users taking a course or a Group of users so that `participants` can `collaborate`

\> Create a `group of users`, assign learning material, courses and quizzes to them, and `track their progress or scores` against Courses.

\> Send `notifications to a set of users` about new content / activities that have been added on the platform&#x20;



Various components of _Lern_ permit for different configurations, allowing the system to enable various workflows as required. Learn about the configurations that each component allows for, on the page for the specific component, as enumerated on the left panel.
