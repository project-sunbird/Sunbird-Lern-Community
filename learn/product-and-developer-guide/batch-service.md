# BATCH SERVICE

The Batch Service comprises APIs that permit for creation of Batches of users in the context of Collections, allowing for Batch management capabilities (tracking progress of users within a batch, assigning of mentors to batches as well as start and end dates for batches, attaching credentials etc.)



The following are a few sample functionalities that the Batch Service APIs can be used for, on the platform:

* [x] Creation of a new batch for an existing/ new course, so as to track a cohort of users who are expected to take the course
* [x] Configurations for the Batch such as - End date for batch enrolment, certificate criteria (completion of the course and minimum score of 70% for the course assessment) etc.
* [x] Extension of the batch end date if need be
* [x] Enrol and un-enrol from course batch

![](<../../.gitbook/assets/image (3) (2).png>)

There are various configurations that can be made via the Batch Service:

* Batch type : Open (users can enrol by themselves)&#x20;
* Batch Start date and End date and Enrolment End date
* Certificate generation for batch&#x20;
* Criteria for earning a certificate (minimum score for the course assessment)



#### Source Code:

[https://github.com/project-sunbird/sunbird-course-service](https://github.com/project-sunbird/sunbird-course-service)

#### API Documentation:

[Course Batch Management APIs](http://docs.sunbird.org/latest/apis/coursebatchmanapi/)

[Course Enrolment APIs](http://docs.sunbird.org/latest/apis/courseenrolmentapi/)

[Course Progress APIs](http://docs.sunbird.org/latest/apis/courseprogressapi/)

[Course Batch Certificates](http://docs.sunbird.org/latest/apis/coursebatchcertificateapi/)

#### References:

[Courses Infra - Design](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/1493041222)

[Courses](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/632553473)

#### Dependencies:

{% tabs %}
{% tab title="Sunbird Knowlg : Content service" %}
Reading course metadata (content/v1/read)
{% endtab %}

{% tab title="Sunbird Knowlg : Search service" %}
Elastic search service for course metadata (composite/v3/search)
{% endtab %}

{% tab title="Sunbird Inquiry" %}
Fetching metadata of QuestionSet.
{% endtab %}

{% tab title="Sunbird Lern : User&Org Service" %}
To fetch user information for validating the Batch creator and Mentor (user/v1/read)
{% endtab %}
{% endtabs %}

**Adopters:** Diksha

**Contributors**: EkStep

**Last Release Date**: Sep 17 2021

**Version**: 4.2.0
