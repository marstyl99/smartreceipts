# Lovable 2.0 Agent Udemy Tutorial

This repository contains the source code generated using [Lovable.dev](https://lovable.dev), enhanced with Supabase, Google OAuth, custom email and our own domain.

> **Project Link:** [Open in Lovable](https://lovable.dev/projects/75eef624-36f8-4165-be51-3080740e23ae)

---

## Quick Start

### 1. Create a Supabase account

1. Go to [Supabase](https://supabase.com) and create a new organization.
2. Name it however you want. Usually tha name of your project.
3. In Lovable:
   - On the main screen, click on the Supabase button, and connect the organization you created earlier with the app.
---

### 2. Set up Google OAuth with Supabase

1. Go to your [Google Cloud Console](https://console.cloud.google.com/):
   - Click view all products.
   - Click Google Auth Platform
   - Create a new project (or reuse one)
   - Enable **OAuth 2.0 Consent Screen** by clicking **Get Started**
   - Add your app's name and your email
   - Pick **External**
   - Create **OAuth Client ID**:
     - Application type: Web
     - Pick you app's name
     - Click on **Authorized redirect URI** and add :  
       `https://<your-supabase-project>.supabase.co/auth/v1/callback` from Supabase/Authentication/Sign-in/Providers/Google
     - Copy the **Client ID** and **Client Secret**
    
3. In Supabase:
   - Go to **Authentication > Providers > Google**
   - Add your **Client ID** and **Client Secret**
   - Save

---

### 3. Connect Custom Domain (e.g. smartreceipts.site)

1. In Lovable:
   - Navigate to **Project > Settings > Domains**
   - Click **Connect Domain**
2. Follow the DNS setup instructions provided by Lovable.
3. Once DNS propagates, your domain (e.g. `https://www.smartreceipts.site`) will serve your app.

More info: [Custom Domain Docs](https://docs.lovable.dev/tips-tricks/custom-domain#step-by-step-guide)

---

### 4. Customize Emails & Custom Email SMTP 

1. In **Supabase**:
   - Navigate to **Auth > Email Templates**
   - Edit the following templates:
     - **Confirm signup**  
     - **Password reset**  
     - **Magic link login**  
     - **Invite user**

2. For custom email, set up **Cloudflare Email Routing**:
   - Connect your domain to CloudFlare's nameservers
   - Then, go to **Cloudflare Email Routing**
   - Route **noreply@smartreceipts.site** → your real inbox (e.g. Google email)

4. Add SMTP settings in **Supabase > Auth > SMTP Settings**:
   - **SMTP host** (e.g. smtp.mailgun.org or smtp.resend.com)  
   - **SMTP port** (e.g. 587 or 465)  
   - **Sender address** (e.g. noreply@smartreceipts.site)  
   - **SMTP username and password** from resender/mailgun

### 5. Connect GitHub & Run Locally

```bash
# Clone your GitHub repo
git clone <YOUR_REPO_URL>
cd <YOUR_PROJECT_FOLDER>


# Install dependencies
npm install

# Run the dev server
npm run dev
