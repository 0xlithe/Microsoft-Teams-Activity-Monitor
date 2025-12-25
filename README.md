# Microsoft Teams Activity Monitor

A comprehensive web-based tool for monitoring Microsoft Teams user activity and detecting retired & inactive users in your businsess / organization.

##  Features

### 1. **Teams Activity Lookup Tool**
- Check individual user's Teams presence and activity status
- Real-time presence detection (Available, Away, Busy, Offline)
- Last activity timestamp tracking
- History of recent lookups
- Export results to clipboard

### 2. **Retired User Detector**
- Advanced scoring algorithm to identify retired employees.
- Single user or bulk analysis (up to 50 users)
- Multi-factor retirement risk assessment including:
  - Account status (enabled/disabled)
  - Last sign-in activity
  - Teams presence and activity
  - License assignments
  - Group memberships

##  Prerequisites
- Node.js 14.0+
- Microsoft 365 Organization User with Global Reader permissions
OR
- Microsoft Graph API access with appropriate permissions

##  Start Guide

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/TeamsActivityMonitor.git
cd TeamsActivityMonitor
```

### 2. Install Dependencies
```bash
npm install

### 3. Configure Environment Variables
Copy the `.env.example` file to `.env`:
```bash
cp .env.example .env
```

Edit the `.env` file and add your Microsoft User credentials:
```env
MICROSOFT_CLIENT_ID=your_client_id_here
MICROSOFT_CLIENT_SECRET=your_client_secret_here
MICROSOFT_TENANT_ID=your_tenant_id_here
```

### 4. Run the Development Server
```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

##  Setting Up Microsoft Graph API Access


### EASIEST METHOD: Microsoft 365 Admin Center (Global Reader Permissions)

Go to admin.microsoft.com and sign in.

Left menu: Show all → Roles.

Search Global Reader, open it → Assigned admins. Look for your name.

Or: Users → Active users → open your user → Account tab → Roles → see Admin center access list for Global Reader.

Tip: If you can’t open the admin center, you likely don’t have any admin role (including Global Reader).


### ALTERNATIVE METHOD: REGISTERING AN ACCOUNT WITH AZURE

### Step 1: Register an App in Azure Portal

1. Go to [Azure Portal](https://portal.azure.com)
2. Navigate to **Azure Active Directory** → **App registrations**
3. Click **New registration**
4. Configure your app:
   - **Name**: Teams Activity Monitor
   - **Supported account types**: Accounts in this organizational directory only
   - **Redirect URI**: Leave blank for now
5. Click **Register**

### Step 2: Configure API Permissions

1. In your app registration, go to **API permissions**
2. Click **Add a permission** → **Microsoft Graph**
3. Choose **Application permissions**
4. Add these permissions:
   - `User.Read.All` - Read all users' profiles
   - `Presence.Read.All` - Read presence information
   - `Reports.Read.All` - Read usage reports
   - `Directory.Read.All` - Read directory data
5. Click **Grant admin consent** (requires admin privileges)

### Step 3: Create Client Secret

1. Go to **Certificates & secrets**
2. Click **New client secret**
3. Add a description and select expiry period
4. Click **Add**
5. **Copy the secret value immediately** (it won't be shown again)

### Step 4: Get Your Credentials

From the app overview page, copy:
- **Application (client) ID** → `MICROSOFT_CLIENT_ID`
- **Directory (tenant) ID** → `MICROSOFT_TENANT_ID`
- Your copied secret → `MICROSOFT_CLIENT_SECRET`


### PowerShell Guide
1. Navigate to `/powershell-guide`
2. Follow the step-by-step instructions
3. Copy code snippets as needed
4. Use for advanced Teams management tasks

##  Retirement Detection Algorithm

The tool uses a weighted scoring system to assess retirement risk:

| Indicator | Weight | Description |
|-----------|--------|-------------|
| Account Status | 30% | Checks if account is disabled or blocked |
| Last Sign-in | 25% | Days since last authentication |
| Teams Activity | 20% | Recent Teams presence and activity |
| License Status | 15% | Active licenses and usage |
| Group Membership | 10% | Active directory and security groups |


### Technology Stack
- Frontend: NextJS 14, React 18, TailwindCSS
- API Integration: Microsoft Graph API

