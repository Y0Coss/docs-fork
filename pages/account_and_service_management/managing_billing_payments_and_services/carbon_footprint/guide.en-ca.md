---
title: "How getting the carbon footprint of your OVHcloud services"
excerpt: "Find out how to recover the monthly carbon footprint of Bare Metal services using our carbon calculator"
updated: 2025-02-17
---

## Objective

As part of your professional activities or out of interest on the subject, you may need to calculate the carbon footprint of your services.

**Find out how to recover the monthly carbon footprint of Bare Metal services linked to your OVHcloud NIC handle.**

## Requirements

- at least one [Dedicated Server](/links/bare-metal/bare-metal) (Advance, Game, Scale, High Grade, Storage) or one [Eco Dedicated Server](/links/bare-metal/eco) (Rise, Kimsufi, So you Start) eligible for the carbon footprint calculation.
- Be a “Billing” contact for the service(s) you would like to create a carbon footprint for. For more information, see [our guide to managing contacts](/pages/account_and_service_management/account_information/managing_contacts).

## Instructions

### You can retrieve the monthly balance sheet for the previous month via the OVHcloud Control Panel

To do this, perform the following steps:

1\. Log in to the [OVHcloud Control Panel](/links/manager).
1\. Click on your account name in the top right-hand corner, then click on your name again in the sidebar that appears on the right-hand side.
1\. On the new page that opens, click on the `My Carbon Footprint`{.action} tab in the left-hand column.
1\. On the page that appears, click `Download my [Month] [Year] footprint`{.action}.

![Carbon footprint](/pages/assets/screens/control_panel/product-selection/right-column/carbon-footprint/my-carbon-footprint.png){.thumbnail}

> [!warning]
>
> You cannot generate a balance sheet for the current month. The only review available via the OVHcloud Control Panel is the one from the previous month.

You can recover the carbon footprint of the previous month for your eligible services every month.

If you need the carbon footprint for a month before the current month, you will need to use our APIs to retrieve it.

### Retrieve a monthly balance sheet prior to the previous month via our APIs

By default, OVHcloud APIs are made available to developers or integrators to associate features, such as those not present in the OVHcloud Control Panel, directly with their applications or solutions.

### Step 1 - Log in to the OVHcloud APIs and give them access to your services

To do this, perform the following steps:

- Go to our website [OVHcloud API](/links/api) (check that you are on `https://eu.api.ovh.com` if your services are hosted in Europe, and on `https://ca.api.ovh.com` if they are hosted outside Europe).
- On the page that pops up, middle-click `Explore the OVHcloud API`{.action}.
- On the new page that appears, and on the left-hand side of the page, go to the form to the right of the form `v1`{.action}, then select/enter the choice `/me`.
- From the list of APIs that appears below in the left-hand column, locate and click on the following API: **POST /me/carbonCalculator/task**. You can also access it directly via the API call below:

> [!api]
>
> @api {v1} /me POST /me/carbonCalculator/task
>

- On the right-hand side of the page, you will then see the API with its box to complete.
- Click the button in the top right-hand corner labeled `Authenticate`{.action}, then the `Login with OVHcloud SSO`{.action} button.
- The interface for connecting to your [OVHcloud Control Panel](/links/manager) will open.
- Log in with your NIC handle, then click `Authorize`{.action} to use the OVHcloud APIs with the services in the OVHcloud Control Panel.
- You will then be automatically redirected to the previous page of the **POST /me/carbonCalculator/task** API, while you are logged in to the OVHcloud Control Panel.

#### Step 2 - Request Balance Sheet Generation and Retrieve the Requested Task ID

To do this, replace the current date that appears in the API sidebar with the date on which you want to stop calculating the balance sheet. Please respect the following date format:

```bash
{
  "date": "YYYY-MM-DD"
}
```

![API](/pages/assets/screens/api/post-me-carboncalculator-task.png){.thumbnail}

> [!warning]
>
> There are several points to keep in mind:
>
> - You cannot generate a balance sheet for the current month.
> - Whether you enter a date at the beginning, middle or end of the month for the month chosen, the balance sheet will take into account the full month.
> - No balance sheets can be generated after the last 24 months.
> - No balance sheet can be generated before May 2023 (date when the feature was set up).

Once you have chosen the correct date, click on the blue `EXECUTE`{.action} button in the bottom right-hand corner of the previously filled-in section.

If everything has been done correctly, a `taskID` will appear in the `RESPONSE`{.action} window when you go down the page below the `EXECUTE`{.action} button.

![API](/pages/assets/screens/api/post-me-carboncalculator-task-response.png){.thumbnail}

For example, if your OVHcloud NIC handle is `aa00000-ovh` and the date you selected earlier was `2025-01-31`, then you will get the following result:

```bash
{
  "taskID": "aa00000-ovh_202501"
}
```

Copy only the value you get from your side and equivalent to the value of our example `aa00000-ovh_202501` (without copying the two `"` located at the ends).

#### Step 3 - Retrieve the file containing the carbon footprint of your services in PDF format

Thanks to the `taskID` value previously retrieved, you can retrieve the carbon balance of your services in PDF format.

To do this, stay on our website [OVHcloud API](/links/api) and perform the following actions:

- On the left-hand side of the page, go to the form to the right of the form `v1`{.action}, then select/enter the choice `/me`{.action}.
- From the list of APIs that appears below in the left-hand column, locate and click on the following API: **GET /me/carbonCalculator/task/{taskID}**. You can also access it directly via the API call below:

> [!api]
>
> @api {v1} /me GET /me/carbonCalculator/task/{taskID}
>

- On the right-hand side of the page, you will then see the API with a form to fill in.

Complete the form in the `PATH PARAMETERS` section as follows:

- `taskID`: Copy here the taskID value retrieved earlier in step 2.

![API](/pages/assets/screens/api/get-me-carboncalculator-task-taskid.png){.thumbnail}

Once you have entered the value for your `taskID` correctly, click on the blue `EXECUTE`{.action} button in the bottom right-hand corner of the previously filled-in section.

The following result appears in the `RESPONSE`{.action} window when you scroll down the page below the `EXECUTE`{.action} button:

![API](/pages/assets/screens/api/get-me-carboncalculator-task-taskid-response.png){.thumbnail}

```bash
{
  "link": "Find here the complete URL to download the carbon footprint in PDF format",
  "status": "SUCCESS",
  "taskID": "aa00000-ovh_202501"
}
```

In this result, copy the entire URL in "HTTPS" (**without the quotation marks**) on the right-hand side of the comment `"link":`, then paste it into the search bar of your web browser to start downloading the carbon footprint in PDF format.

Your web browser will automatically download the file and then display it.

> [!primary]
>
> Depending on your browser’s configuration, the file may not be able to download and display properly. If this is the case, check your browser configuration, then reload the page.

Once the file is open, you will find, among other things, the following elements:

- A summary table of C02 emissions by category for the requested month via our APIs.
- A summary table of C02 emissions by category between the beginning of the calendar year and the requested month via our APIs.
- A table detailing the values by type of product subscribed.
- A graph showing C02 emissions by category.

## Go further <a name="go-further"></a>

[First Steps with the OVHcloud APIs](/pages/manage_and_operate/api/first-steps)
 
For specialised services (SEO, development, etc.), contact [OVHcloud partners](/links/partner).
 
Join our [community of users](/links/community).