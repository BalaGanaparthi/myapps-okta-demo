User must be able to registered for a digital account with basic demographic information (First name, Last Name, Email, Password)
User can login to a central MyApps application with the digital account credentials
Develop mock app for Central MyApps, InterOP, BlueAccess-Member, BlueAccess-Non-Member, BlueAccess-Employer, BlueAccess-Broker and InterOp
When the user clicks on login, initiate the login to the Central MyApps application
Once the user login is successful and
If the user do not have permission to any apps (no claims with digital apps identifiers like mpn, npn, memId, GrpNum, fhirPID), then show page with available apps,
if the permission available then show tiles for the permitted apps (if memid/group# then show BlueAccess-Member, if MPN# then BlueAccess-Employer, if NPN# then BlueAccess-Broker and if fhirPID then show InterOp)
If the user clicks on Available apps and clicks any one app (Member, Non-Member, Broker, Employer or InterOp), launch the login endpoint of respective app which inturn the app’s login page constructs the /authorize url with the clientId and executes the 302 redirect, where Okta will perform progressive profiling to collect any required data from the user but do not prompt for the password as the user must have an active okta session
If the user clicks any of the permitted apps, launch the login endpoint of the app where the app receiving the call will compose a /authorize url with the clientID and executes a 302 redirect where the user is directly login without any additional prompts.
