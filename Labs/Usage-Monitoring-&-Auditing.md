# Usage Monitoring & Auditing

Let’s use Power BI   audit Log to answer a few questions.

### Problem: Data is leaked to the internet. How to identify the issue?

1. Open PowerBIAuditLog.pbix (file located in Assets folder). 

2. Publish to Web is a feature where data can be accessed without entering credentials. So, let’s look for this activity.

3. From Activity slicer, select to PublishToWebReport.

![Publish to web](Images/PublishToWeb.png)

4. Notice there a few users who have published to web. 

5. Publish to web might be a legimate requirement but you will want to track who is publishing to the web so you monitor and take action if necessary. You can work with these users to investigate further.


### Dashboards and Reports are being deleted. Who is doing it?

1. From Activity slicer, select to DeleteDashboard and DeleteReport.

![Publish to web](Images/DashBoardsDeleted.png)

2. This will give a list of users who have deleted reports and dashboards. You can work with these users and investigate further.

3. Remove all filters once done.

