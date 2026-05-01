# EduFlow Postman Suite

Use these files together:
- [EduFlow_Complete.postman_collection.json](/E:/lms-platform/lms-dev-environment/docs/postman/EduFlow_Complete.postman_collection.json)
- [EduFlow_Local_Complete.postman_environment.json](/E:/lms-platform/lms-dev-environment/docs/postman/EduFlow_Local_Complete.postman_environment.json)

## What changed
- The collection now stores `permissions` for student, instructor, and admin tokens.
- Role-management requests now match the current gateway contract and permission-based auth checks.
- The role-permission flow includes listing permissions, adding a permission with the current array-body API, and removing it again.

## Start services
- Service registry on `http://localhost:8761`
- API gateway on `http://localhost:8080`
- Auth service registered behind the gateway
- User service registered behind the gateway

## Recommended run order
1. `Flow 1: Registration & Onboarding`
2. `Flow 2: Authentication Core`
3. `Flow 3: Role & Permission Management`
4. `Flow 4: User Management`
5. `Flow 5: Gateway Security Verification`

## What is automated
- Register, login, refresh, and validate flows for student, instructor, and admin
- Token and permission variable storage
- Role creation, permission creation, permission assignment, permission removal, and role cleanup
- Gateway-level protected-route checks for student and instructor denial cases

## Environment notes
- Seeded positive-path accounts still assume `admin@lms.com` / `Password123`.
- Instructor positive-path requests still assume `instructor@lms.com` / `Password123`.
- The environment now includes `studentPermissions`, `instructorPermissions`, `adminPermissions`, `testRoleName`, and `testPermissionName`.

## Current repo caveat
- `auth-service` JWTs carry numeric user IDs.
- `user-service` route IDs are harvested from user-service responses.
- Because auth IDs and user-service IDs do not match, self-profile requests can pass gateway authorization and still fail downstream.
- The collection keeps treating `not 401/403` as the gateway-success condition for those self-access checks.
