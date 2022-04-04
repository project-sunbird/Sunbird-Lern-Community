# Tech Design of The Component

#### **Architecture Diagram**

![](<../../../.gitbook/assets/image (3).png>)

1. **CRUD** operations are managed by **Group Service**.
2. From Group Service If the API is related to the **user/member** then the **Learner Service** is called to get the user details.
3. &#x20;Notifications are created by Notification Service for some action in groups (eg: Group Created).
4. &#x20;**Content Service** is **** used to get all the results based on the  Search Query.
5. **Cassandra Databas**_**e**_ is used to do all the CRUD operations.
6. All the Telemetry Data are stored in **Kafka**
