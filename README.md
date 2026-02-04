# App Request Portal

A self-service app request solution for Microsoft Intune. Enable your users to browse and request software deployments through an intuitive web portal, with configurable approval workflows and automatic Azure AD group management.

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FPowerStacks-BI%2FApp-Request-Portal-Releases%2Fmain%2Fazuredeploy.json)

## Features

- **Self-Service App Catalog** - Users browse and request apps from your Intune library
- **Approval Workflows** - Configurable multi-stage approvals with manager and group-based routing
- **Automatic Group Management** - Creates Azure AD groups and Intune assignments automatically
- **Email Notifications** - Notify requesters and approvers at each workflow stage
- **Dark Mode** - Admin-configurable with user override option
- **Reports & Analytics** - ROI calculator, usage reports, and approval metrics
- **Branding** - Customize logo, colors, and text to match your organization
- **Winget Integration** - Browse and publish apps from the Windows Package Manager catalog

## Prerequisites

Before deploying, you'll need:

1. **Azure Subscription** with permissions to create resources
2. **Azure AD App Registrations** (2 required):
   - **API Application** - For backend authentication and Microsoft Graph access
   - **Frontend SPA Application** - For user authentication

### Required Azure AD Permissions

The **API Application** requires these Microsoft Graph **Application permissions** with admin consent:

| Permission | Purpose |
|------------|---------|
| `DeviceManagementApps.Read.All` | Read Intune apps |
| `DeviceManagementApps.ReadWrite.All` | Create app assignments |
| `DeviceManagementManagedDevices.Read.All` | Read user devices |
| `Group.ReadWrite.All` | Create and manage groups |
| `User.Read.All` | Read user profiles |
| `Directory.Read.All` | Read directory data |
| `Mail.Send` | Send email notifications (optional) |

## Quick Start

### Step 1: Create Azure AD App Registrations

1. **Create the API Application**:
   - Go to Azure Portal > Azure Active Directory > App registrations > New registration
   - Name: `App Request Portal API`
   - Supported account types: Single tenant
   - Add the Graph API permissions listed above
   - Create a client secret and save it securely
   - Note the **Application (client) ID**

2. **Create the Frontend Application**:
   - Go to Azure Portal > Azure Active Directory > App registrations > New registration
   - Name: `App Request Portal`
   - Supported account types: Single tenant
   - Redirect URI: `https://your-app-url.azurewebsites.net` (update after deployment)
   - Platform: Single-page application (SPA)
   - Note the **Application (client) ID**

### Step 2: Deploy to Azure

Click the button below to deploy the portal to your Azure subscription:

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FPowerStacks-BI%2FApp-Request-Portal-Releases%2Fmain%2Fazuredeploy.json)

Fill in the required parameters:
- **Tenant ID** - Your Azure AD tenant ID
- **API Client ID** - From Step 1
- **API Client Secret** - From Step 1
- **Frontend Client ID** - From Step 1
- **SQL Admin Password** - Create a strong password (12+ characters)

### Step 3: Update Redirect URIs

After deployment completes:
1. Copy the **Portal URL** from the deployment outputs
2. Go to Azure AD > App registrations > Your frontend app > Authentication
3. Add the portal URL as a redirect URI

### Step 4: Complete Setup Wizard

1. Visit your portal URL
2. Sign in with an Azure AD account
3. Complete the **Setup Wizard**:
   - Enter your PowerStacks license key
   - Configure admin and approver groups
   - Set up email notifications (optional)
   - Sync apps from Intune

## Custom Domain (Optional)

To use a custom domain like `apps.yourdomain.com`:

1. Configure DNS (CNAME pointing to your App Service)
2. Deploy the custom domain template:

[![Deploy Custom Domain](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FPowerStacks-BI%2FApp-Request-Portal-Releases%2Fmain%2Fazuredeploy-customdomain.json)

## Documentation

- [Admin Guide](https://github.com/PowerStacks-BI/AppRequestPortal/blob/main/docs/ADMIN-GUIDE.md)
- [Deployment Guide](https://github.com/PowerStacks-BI/AppRequestPortal/blob/main/docs/DEPLOYMENT.md)
- [Custom Domains](https://github.com/PowerStacks-BI/AppRequestPortal/blob/main/docs/CUSTOM-DOMAINS.md)
- [Approval Workflows](https://github.com/PowerStacks-BI/AppRequestPortal/blob/main/docs/APPROVAL-WORKFLOWS.md)

## Support

- **Issues**: [GitHub Issues](https://github.com/PowerStacks-BI/AppRequestPortal/issues)
- **License**: Contact [PowerStacks](https://powerstacks.com) for licensing

## License

This software requires a valid PowerStacks license. Contact [powerstacks.com](https://powerstacks.com) for licensing information.

---

Built by [PowerStacks](https://powerstacks.com)
