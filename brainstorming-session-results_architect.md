# Brainstorming Session Results

**Session Date:** 25/08/2025
**Facilitator:** Business Analyst Mary
**Participant:** User

---

## Executive Summary

**Topic:** Building a high-performance, scalable e-commerce website for selling perfumes, with an initial inventory of 350 products.

**Session Goals:** The primary goal was to focus on technical solutions to ensure fast page load times and an optimized, frictionless checkout process, laying the groundwork for Phase 1 development.

**Techniques Used:**
1.  **Reverse Brainstorming:** To proactively identify potential problems that could degrade performance and user experience.
2.  **Benefit-Cost-Mitigation Analysis:** To evaluate proposed solutions and select the most optimal technical architecture.

**Key Themes & Decisions:**
*   **Performance is paramount:** Identified unoptimized images and inefficient data loading as the biggest threats to site speed.
*   **Frictionless checkout is critical:** Determined that mandatory login, complex forms, and hidden costs are major deterrents for customers.
*   **A Serverless-First architecture on AWS is the optimal path forward:** This approach maximizes cost-efficiency (leveraging extensive Free Tiers), performance, and scalability while minimizing operational overhead.

---

## Identified Risks & Problems (Reverse Brainstorming)

### 1. Website Performance Degradation
*   **Problem:** Using large, unoptimized original image files directly on the website.
*   **Problem:** Loading all 350 product images on initial page load, regardless of user interaction (i.e., no "lazy loading").
*   **Problem:** Storing static assets (images, CSS, JS) on a single origin server located far from the target user base in Vietnam.

### 2. Checkout Process Abandonment
*   **Problem:** Forcing users to create an account or log in before they can make a purchase.
*   **Problem:** Requiring users to fill out long, complicated forms with non-essential information.
*   **Problem:** Surprising users with unexpected shipping fees or taxes only at the final step of the checkout process.

---

## Proposed Technical Architecture & Solutions

### Recommended Architecture: **Serverless-First on AWS**

This architecture was chosen for its alignment with the project's key requirements: high performance, scalability, and extreme cost-efficiency for the initial phase.

**Diagram:**
```
User (Browser)
      │
      ▼
┌──────────────────┐
│   AWS CloudFront   │ (CDN for Static Content & API)
└─────────┬────────┘
          │
    ┌─────┴──────┐
    │            │
    ▼ (Static)   ▼ (Dynamic API Requests)
┌───────────┐   ┌────────────────┐
│ S3 Bucket │   │  API Gateway   │
└───────────┘   └────────┬───────┘
                         │
                         ▼
                  ┌────────────────┐
                  │  AWS Lambda    │ (Business Logic)
                  └───────┬────────┘
            ┌─────────────┴──────────────┐
            │                            │
            ▼                            ▼
      ┌──────────┐                 ┌───────────┐
      │ DynamoDB │                 │  Cognito  │ (User Management)
      └──────────┘                 └───────────┘
```

### Component Analysis & Justification

*   **Frontend Hosting (S3 + CloudFront):**
    *   **Benefit:** Delivers best-in-class speed by serving static files (HTML, CSS, JS, images) from CloudFront's global edge network, with a Point of Presence in Vietnam. Extremely low cost and infinitely scalable.
    *   **Cost:** Minimal. Covered by the generous AWS Free Tier (1TB data transfer/month).
    *   **Mitigation:** This architecture directly solves the identified problems of asset loading speed and server location.

*   **Backend Logic (API Gateway + AWS Lambda):**
    *   **Benefit:** A "pay-as-you-go" model. Code only runs when an API request is made, meaning zero cost for idle time. Auto-scales to handle traffic spikes without any manual intervention. Eliminates server management overhead.
    *   **Cost:** Minimal. Covered by the Free Tier (1 million requests/month for both services). This is far more cost-effective than a constantly running EC2 instance for a new website.
    *   **Mitigation:** Provides a scalable, cost-effective engine for all core e-commerce functions (search, cart management, checkout).

*   **Database (Amazon DynamoDB):**
    *   **Benefit:** A fully managed, serverless NoSQL database that offers single-digit millisecond latency. Pairs perfectly with Lambda for high-performance applications.
    *   **Cost:** Minimal. Covered by the Free Tier (25GB storage, ~200 million requests/month).
    *   **Mitigation:** Provides a fast and scalable database for products, orders, and user data.

*   **User Management (Amazon Cognito):**
    *   **Benefit:** Offloads the complex and critical work of building and maintaining user authentication (sign-up, sign-in, password reset). Secure and fully managed.
    *   **Cost:** Minimal. Free for the first 50,000 monthly active users.
    *   **Mitigation:** Directly enables a smooth "guest checkout" flow while still offering a secure, easy way for users to create accounts if they choose.

---

## Action Plan & Next Steps

1.  **Finalize Phase 1 Feature List:** Refine the core features needed for launch based on this architecture.
2.  **Set up AWS Environment:** Create the necessary S3 buckets, configure CloudFront, set up DynamoDB tables, and initialize a Cognito User Pool.
3.  **Develop Backend API:** Begin writing Lambda functions for core functionalities (e.g., `getProduct`, `createOrder`).
4.  **Develop Frontend Application:** Build the user interface that will consume the backend API.
5.  **Implement Image Optimization Pipeline:** Create the Lambda function triggered by S3 uploads to automate image processing.
