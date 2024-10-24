# Gitea Usage Documentation for Nextgen Techno

This document outlines the steps for accessing, using, and managing projects on Gitea, hosted at `lab.nextgentechno.in`. The platform is primarily used by the Nextgen Techno team for product and service development, with specific guidelines for CI/CD workflows and user management.

## 1. Accessing Gitea
To access Gitea, follow the steps below:

- Visit [lab.nextgentechno.in](https://lab.nextgentechno.in).
- Use the following credentials to log in as the Superadmin:
  - **Username**: `superadmin`
  - **Password**: `1234567`

### Note: 
Only authorized personnel should use the Superadmin account, primarily for administrative tasks such as managing users and organizations.

## 2. User Signup Process
Users who are part of Nextgen Techno must sign up using NextgenAuth. Follow these steps to create an account:

1. **Click on the “Sign in with NextgenAuth” button**: This will redirect you to NextgenAuth's authentication portal.
2. **Authenticate using your NextgenAuth credentials**: Enter your authorized company credentials.
3. **Post-authentication**: Once signed in, Gitea will prompt you to **create a password** for accessing the platform.
   - Choose a secure password that adheres to Nextgen’s security policy.
   - This password will be required for future logins to Gitea.

### Note:
Signing up via NextgenAuth ensures that all users are properly authenticated and linked to their corporate identity.

## 3. User Management
Only **Superadmins** or **CEOs** have the authority to manage users, including assigning them to specific organizations. If you require access to a particular organization, please contact the Superadmin or CEO with the following information:

- Your Gitea username.
- The organization you need access to (e.g., `Nextgen Vidhya` or `Nextgen Techno`).

Once approved, the Superadmin or CEO will add you to the appropriate organization.

### Organizations on Gitea:
- **Nextgen Vidhya**: This organization contains all the project code related to products.
- **Nextgen Techno**: This organization contains all the project code related to services.

## 4. CI/CD Workflow

### Branches in Gitea:
The workflow for handling the Continuous Integration and Continuous Deployment (CI/CD) process on Gitea follows a structured approach. The branches involved are:

1. **dev branch**: 
   - Developers create pull requests (PRs) and work on new features or bug fixes in this branch.
   - Code changes are regularly merged here.

2. **Main branch**:
   - Once the PRs from `dev branch` are reviewed and closed, they are merged into the `Main` branch.
   - This branch always contains the latest code changes.

3. **Beta branch**: 
   - After testing on the `Main` branch, the changes are pushed to the `Beta` branch for final testing and staging.

4. **Production branch**:
   - The production-ready code is merged into the `Production` branch.
   - Only thoroughly tested and approved code is deployed here.

### CI/CD Flow Summary:
1. All work begins on the **dev branch**.
2. Code is merged into **Main** after a successful pull request.
3. From **Main**, it flows into **Beta** for staging.
4. Finally, it reaches **Production** for deployment.

### Note:
Always ensure that the latest code changes are found in the **Main branch**. This branch serves as the primary codebase for all updates.

## 5. Best Practices for Gitea Usage

- **Branch Naming**: Follow the naming convention for branches to make the CI/CD flow smoother:
  - Feature branches: `feature/<name-of-feature>`
  - Bugfix branches: `bugfix/<name-of-bugfix>`
  - Hotfix branches: `hotfix/<name-of-hotfix>`

- **Pull Requests (PRs)**: Always submit pull requests for code reviews. Ensure that code changes are thoroughly tested before being merged into the `Main branch`.

- **Commit Messages**: Use meaningful commit messages that clearly explain the purpose of the commit. This ensures easy traceability of changes.

## 6. Superadmin Responsibilities

Superadmins have additional responsibilities, including:
- Managing user access to organizations.
- Approving and closing pull requests.
- Enforcing the CI/CD workflow.
- Ensuring that the latest code remains up-to-date in the `Main branch`.

### Adding Users to Organizations:
- Go to the **Admin Panel**.
- Navigate to **Users** and select the user to be added.
- Under **Organizations**, select the appropriate organization (`Nextgen Vidhya` or `Nextgen Techno`) and assign the user.

## 7. Conclusion
By following the procedures outlined in this document, you can ensure smooth collaboration and efficient use of Gitea at `lab.nextgentechno.in`. Make sure to adhere to the CI/CD workflows, use the appropriate branches, and seek assistance from Superadmins or the CEO when needed.