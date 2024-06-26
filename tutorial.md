# Comm-IT GCP Onboarding


## Let's get started!

We're going to go through a few short steps to get you set up and working with the Comm-IT GCP team!

**Time to complete**: About 5-10 minutes

Click the **Start** button to move to the next step.

## Step 0 - Login 

Let's make sure you're logged in and able to use the gcloud CLI. If you're already logged in, you can skip this step. 

To login, execute the following command:

```bash
gcloud auth login
```

You will be prompted to navigate to an authentication page. Once you sign in there, you will receive a code, which you must paste back into the terminal, at the prompt. Once you're done, you should see a message that looks like: "You are now logged in as [<YOUR_EMAIL_ADDRESS>]"

Click "Next" when you've finished.

## Step 1 - Read Only Permissions on Organization

The first step is to grant read-only permissions to Comm-IT's support team on the customer's organization. We recommend that the client give us permissions as viewers so that our support team can provide a better service, however this is not mandatory. There are clients who prefer not to provide these permissions for compliance or privacy reasons. If you would like to skip this step, click "Next" below without executing the steps in this slide. 

To grant the permissions, execute the following command:

```bash
./1_organization_permissions.sh
```

**Tip**: Click the copy button on the side of the code box and paste the command in the Cloud Shell terminal to run it.

You will be prompted for your Organization ID. To find this, in the GCP Console, in the top toolbar, left of the search bar, click the dropdown menu and go to the "ALL" tab. Your Organization ID should be next to your Organization name. If you need help, look at the README.md in the GitHub repository for a picture that shows where to find this.

Click "Next" when you've finished.

## Step 2 - Billing Administrator Permissions

In order to migrate the projects to our sub-billing account we will need Billing Administrator permissions in the customer's projects.

To grant the permissions, execute the following command:

```bash
./2_billing_project_manager.sh <PROJECT_ID_1> <PROJECT_ID_2> <PROJECT_ID_3> ...
```

**Tip**: Click the copy button on the side of the code box and paste the command in the Cloud Shell terminal to run it.

You must provide project IDs as arguments to the script, as shown above. To find a project ID, in the GCP Console, in the top toolbar, left of the search bar, click the dropdown menu and find your project name. Its project ID should be next to its name (these are often the same, but not always). Save these project IDs for the next step! If you need help, look at the README.md in the GitHub repository for a picture that shows where to find this.

Click "Next" when you've finished.

## Step 3 - Move Project to Sub-Billing Account

We need to link the customer's projects to the customer's sub-billing account. To link the projects to the billing account, execute the following command:

```bash
./3_link_billing_account.sh <PROJECT_ID_1> <PROJECT_ID_2> <PROJECT_ID_3> ...
```

**Tip**: Click the copy button on the side of the code box and paste the command in the Cloud Shell terminal to run it.

These are the same project IDs you provided in the last step.

You will be prompted for a Billing Account ID. To find this, go to the Billing page: https://console.cloud.google.com/billing and click on the name of the desired sub-billing account, and go to "Account Management" in the toolbar on the left.

Click "Next" when you've finished.

## Step 4 - Close Old Billing Account

In order to avoid confusion, we will close the old billing account. To find this, go to the Billing page: https://console.cloud.google.com/billing and click on the name of the old billing account. Go to “Account Management” in the toolbar on the left, and you will see the option to “Close Billing Account” near the top of the page, under the search bar. 

Click "Next" when you've finished.

## Step 5 - Create Billing Project

Now we are going to create a billing export project and assign Owner permissions on the project to the Comm-IT team. This project will be used to create a Looker Studio Dashboard for cost analysis. If you do not want this, click "Next" without executing the steps.

To create the project and grant the permissions, execute the following command:

```bash
./5_billing_export_project.sh
```

**Tip**: Click the copy button on the side of the code box and paste the command in the Cloud Shell terminal to run it.

You will be prompted for a project ID to create a new project. The name should follow the convention companyname-billing. Please record the name that you provide. Then you will be prompted for the email of the Comm-IT User or Group to whom you wish to give the Owner role on the project. 

Click "Next" when you've finished.

## Congratulations

<tutorial-conclusion-trophy></tutorial-conclusion-trophy>

You’re all set! Please be in touch with a Comm-IT team member for next steps.

