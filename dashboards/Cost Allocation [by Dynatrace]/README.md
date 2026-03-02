# DPS Cost Allocation Dashboard

## Overview
**Understand your costs. Stay in control.**

The **Cost Allocation Dashboard** helps you break down and explore usage and cost data per environment — giving you the transparency you need to manage resources effectively.

With this dashboard, you can:
- View total usage and costs for any selected period.
- Apply service fees on top of Dynatrace rate cards — different dashboards can use different rate card configurations.
- Track how costs evolve over time.
- Drill down by cost center or product.
- Trace each usage item back to its source.

Whether you're showing costs back to teams or investigating optimization opportunities, the dashboard gives you the visibility to make informed decisions.

**Simple. Transparent. Secure.**

Before using the Cost Allocation Dashboard, make sure you have configured [Dynatrace Cost Allocation](https://community.dynatrace.com/t5/DPS-Cost-Allocation/).

For questions and support, join the conversation in the [Dynatrace Community](https://community.dynatrace.com/t5/DPS-Cost-Allocation/).

<img width="1919" height="1199" alt="Screenshot 1" src="https://github.com/user-attachments/assets/771353df-2f85-4334-92da-e352c52a6346" />

---

## 🎯 Purpose
The **DPS Cost Allocation Dashboard** helps organizations:
- Understand how their usage of Dynatrace capabilities, linked to their DPS license, is distributed across customer-defined cost centers.
- Optimize resource allocation and usage.
- Support chargeback and show-back use cases between teams or departments within an organization.

The dashboard allows you to view your current cost-field enrollment status, along with the usage and expenses associated with each supported capability. Use the **top left section** to navigate between different capabilities. The variables in the **top middle area** enable you to adjust the pricing according to your rate card.

You can also use this dashboard as a foundation to create your own usage and cost summaries, which can then be shared internally with your colleagues.

---

## 📊 What You’ll See
The dashboard includes the following visualizations:
- **Estimated Cost Distribution per Capability (Pie Chart):** Visualizes the cost distribution across different capabilities.
- **Estimated Costs per Cost Center or Product (Pie Chart):** Displays the cost distribution across various cost centers or products.
- **Total Costs (Single Value):** Shows the total cost for the selected timeframe.
- **List of Usage and Estimated Costs (Table):** Provides a detailed breakdown of usage and costs per capability and cost center.

---

## ⚙️ Getting Started

### Prerequisites
Before you begin, ensure you have:
- A Dynatrace environment with access to the Dashboards app.
- Appropriate permissions to import and edit dashboards.
- Appropriate permissions to view System Events.
- DPS Cost Allocation properly set up.

### Installation Steps
1. **Download the JSON File**  
   [Download Here](<ONE LINK here>)

2. **Import the Dashboard:**
   - Open the **Dashboards** app in your Dynatrace environment.
   - Click on **Import dashboard** and upload the downloaded JSON file.

3. **Adjust Variables:**
   - Ensure the `ratecard_data` variable is correctly configured. You can either set it up with values from your Dynatrace subscription or define the rate card for your internal customers.
   - Modify the namespace and cluster filters if your environment differs.

4. **Share and Explore:**
   - Share the dashboard with your team and start analyzing your cost data.

---

## 🛠️ Support
For additional help, visit the [Dynatrace Community](https://community.dynatrace.com/t5/DPS-Cost-Allocation/).

---

**Stay in control of your costs with the DPS Cost Allocation Dashboard!**
