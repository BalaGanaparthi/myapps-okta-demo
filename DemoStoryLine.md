## 1. New User Registration

Test User with {FN : Test, LN : User001, Email : test.user001@yopmail.com}

> 1. Okta Admin: Confirm test.user001@yopmail.com is not registered
> 2. localhost:8080 : Visit My Digital Apps and click Siginin
> 3. Okta SignIn : Okta's Signin screen is shown where the user can click on Signup
> 4. Okta Signup : Register user from "My Digital Apps" :: {FN : Test, LN : User001, Email : test.user001@yopmail.com}
> 5. Okta SignIn & Mail Inbox : Verify Email and Set Password
> 6. Okta Admin: Confirm test.user001@yopmail.com is registered and no app specific profile attributes are populated

This confirms that a centralized BCBS Kansas Digital account is created for the user (Slim Profile)

## 2. Existin user accessing MemberApp for the first time

Test User with {Email : test.user001@yopmail.com}

> 1. Okta Admin: Confirm test.user001@yopmail.com is registered but the `MemberID and GroupID` are not populated
> 2. localhost:8080 : Visit My Digital Apps and click Siginin
> 3. Okta SignIn : Enter user's credentials and MFA to login centrally to My Digital Apps Dashboard
> 4. My Digital Apps : Navigate to `My Digital Apps` Section in the app
> 5. My Digital Apps : From the list of apps available for the user, click on the `MemberApp` tile, this launches a new tab in the browser and redirect the user to MemberApp
> 6. MemberApp : Since the Member App will not have an active app session, the app redirects the to Okta, for authentication
> 7. Okta : Since the Okta session is already active (as `My Digital Apps` application have loggein), the user will not be prompted to reauthenticate
> 8. Okta : Okta detects `MemberID and GroupID` as required attributes must exist in the user's profile but are not yet populated, but not yet populated and prompts the users to enter the values (Progressive Profiling)
> 9. Okta : Once the user enters and submits the data, Okta validates (can introduce custom logic) the values and only proceeds further only if values are valid
> 10. Okta : Once the `MemberID and GroupID` are successfully validated, futher process gets executed by issuing tokens to MemberApp for the logged-in user
> 11. MemberApp : MemberApp revcieves the tokens and establishes App Session and allows the user to acccess the app pages
> 12. Okta Admin: Confirm test.user001@yopmail.com is populated `MemberID and GroupID` values that were entered during the MemberApp access

This confirms that a user with centeral digital account can SSO to other qualified apps if they have required policy details (MemberID and GroupID for MemberApp)

## 3. Existing/Returning user accessing revisting MemberApp

Test User with {Email : test.user001@yopmail.com}

> 1. Okta Admin: Confirm test.user001@yopmail.com is registered but the `MemberID and GroupID` are populated
> 2. localhost:8080 : Visit My Digital Apps and click Siginin
> 3. Okta SignIn : Enter user's credentials and MFA to login centrally to My Digital Apps Dashboard
> 4. My Digital Apps : Navigate to `My Digital Apps` Section in the app
> 5. My Digital Apps : From the list of apps available for the user, click on the `MemberApp` tile, this launches a new tab in the browser and redirect the user to MemberApp
> 6. MemberApp : Since the Member App will not have an active app session, the app redirects the to Okta, for authentication
> 7. Okta : Since the Okta session is already active (as `My Digital Apps` application have loggein), the user will not be prompted to reauthenticate
> 8. Okta : Okta detects `MemberID and GroupID` as required attributes are already populated in the user's profile, the user will not be prompted further
> 9. Okta : Futher process gets executed by issuing tokens to MemberApp for the logged-in user
> 10. MemberApp : MemberApp revcieves the tokens and establishes App Session and allows the user to acccess the app pages

This confirms that a user with centeral digital account can SSO to other qualified apps if they have supplied the required policiy details first time during the app access(MemberID and GroupID for MemberApp)
