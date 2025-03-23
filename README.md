# 📊 OTT Merger Analysis: LioCinema & Jotstar
   - [Live Dashboard](https://app.powerbi.com/view?r=eyJrIjoiNmNlMGM5ZWMtYjFmMC00ZjcyLWFkYWItN2M4YWMzOThkZGMyIiwidCI6ImM2ZTU0OWIzLTVmNDUtNDAzMi1hYWU5LWQ0MjQ0ZGM1YjJjNCJ9&pageName=5b362fc122b0b90eb8ee)
   - [Linkedin Post Link]()
   - [Details about complete challenge](https://codebasics.io/challenge/codebasics-resume-project-challenge)
   - [Dashboard PDF version]()

---
## 📌 Overview
Lio, a leading telecommunications provider in India, is planning a strategic merger with Jotstar, one of the country's most prominent streaming platforms. The merger aims to integrate **LioCinema’s expansive subscriber base** with **Jotstar’s diverse content library** to create the leading OTT platform in India. 

This project involves analyzing the **performance and user behavior** of both platforms over the past year (**January to November 2024**) to provide insights that will guide strategic decisions post-merger.

---
## 🔍 Business Problem
The merger between **LioCinema** and **Jotstar** presents a unique opportunity to:
- 🎬 **Optimize content strategies**
- 📈 **Improve subscriber engagement**
- ⚡ **Enhance overall platform performance**

To achieve these objectives, the management team at Lio requires detailed analysis of:
- **📚 Content Library**: Understanding content diversity, genre popularity, and runtime trends.
- **👥 Subscriber Insights**: Trends in subscriber acquisition and demographic variations.
- **⏳ Inactivity Patterns**: Identifying inactivity across different age groups, city tiers, and subscription plans.
- **📊 Upgrade & Downgrade Trends**: Analyzing factors influencing subscription plan changes.
- **📺 Content Consumption Behavior**: Investigating watch time patterns, device preferences, and demographic variations.

---
## 🎯 Key Objectives
- ✅ **Perform a thorough analysis** of the datasets from both platforms.
- ✅ **Identify trends and patterns** in user behavior, content consumption, and subscription changes.
- ✅ **Design a comparison dashboard** that visualizes key insights effectively.
- ✅ **Present findings** in a compelling way to help stakeholders make data-driven decisions.

---
## 🗂️ Dataset Overview
The project uses sample data from two databases: **`LioCinema_db`** and **`Jotstar_db`**, each containing three key tables.

### 📁 LioCinema Database
#### 🎞️ Contents Table
- **`content_id`**: Unique identifier for each content item.
- **`content_type`**: Type of content (e.g., Movie, Series).
- **`language`**: Language in which the content is available.
- **`genre`**: Genre of the content (e.g., Romance, Action, Drama).
- **`run_time`**: Duration of the content in minutes.

#### 👥 Subscribers Table
- **`user_id`**: Unique identifier for each subscriber.
- **`age_group`**: Age group of the subscriber.
- **`city_tier`**: City category of the subscriber.
- **`subscription_date`**: Date when the user subscribed.
- **`subscription_plan`**: Initial subscription plan.
- **`last_active_date`**: Most recent activity date.
- **`plan_change_date`**: Date of subscription plan change.
- **`new_subscription_plan`**: Updated subscription plan.

#### 📺 Content Consumption Table
- **`user_id`**: Unique identifier for each subscriber.
- **`device_type`**: Type of device used to consume content.
- **`total_watch_time`**: Total time spent watching content (mins).

### 📁 Jotstar Database
#### 🎞️ Contents Table
- **`content_id`**: Unique identifier for each content item.
- **`content_type`**: Type of content (e.g., Movie, Series).
- **`language`**: Language in which the content is available.
- **`genre`**: Genre of the content (e.g., Romance, Action, Drama).
- **`run_time`**: Duration of the content in minutes.

#### 👥 Subscribers Table
- **`user_id`**: Unique identifier for each subscriber.
- **`age_group`**: Age group of the subscriber.
- **`city_tier`**: City category of the subscriber.
- **`subscription_date`**: Date when the user subscribed.
- **`subscription_plan`**: Initial subscription plan.
- **`last_active_date`**: Most recent activity date.
- **`plan_change_date`**: Date of subscription plan change.
- **`new_subscription_plan`**: Updated subscription plan.

#### 📺 Content Consumption Table
- **`user_id`**: Unique identifier for each subscriber.
- **`device_type`**: Type of device used to consume content.
- **`total_watch_time`**: Total time spent watching content (mins).

---
## 🗄️Data Model

---
## 📌 Deliverables
- 📌 **Detailed Data Analysis**: Comprehensive insights into content trends, user behavior, and subscription changes.
- 📌 **Comparison Dashboard**: A visual representation of key performance metrics across both platforms.
- 📌 **Presentation**: A well-structured presentation with actionable recommendations for the merger strategy.

---
## 🔍 **Key Insights & Recommendations**

### 🚀 Total Users & Growth Trends  
#### **Key Insights:**  
- **LioCinema** shows steady growth, while **JotStar** experiences fluctuating user acquisition trends.  
- A **noticeable spike** in JotStar's new subscribers in mid-2024, likely due to content releases or marketing campaigns.  
- LioCinema maintains a **consistent upward trajectory**, suggesting strong user retention.  

#### **Recommendations:**  
- **Leverage LioCinema’s retention strategies** to stabilize JotStar’s fluctuating growth.  
- Analyze **mid-2024 spike factors** and replicate successful strategies across platforms.  

---

### 🎬 Content Library Comparison  
#### **Key Insights:**  
- **JotStar has nearly 2x more content** than LioCinema, with **higher average watch time**.  
- **Genre Distribution:**  
  - LioCinema is **drama & comedy-heavy**.  
  - JotStar has a **more diverse mix** (action, thrillers).  
  - Some genres are missing: **Adventure, Fantasy & Sci-Fi (LioCinema), Crime & Horror (JotStar)**.  
- **Language Availability:**  
  - LioCinema focuses on **Hindi, Tamil, Telugu**.  
  - JotStar covers a **wider regional spectrum**, including English.  
- **Content Type & Runtime:**  
  - JotStar has a **larger series library**, while both focus on movies.  
  - **Minimal sports content** on LioCinema.  

#### **Recommendations:**  
- Expand **missing genres** for a **comprehensive library**.  
- **Balance language offerings**—JotStar can increase Hindi/Tamil/Telugu, while LioCinema expands regional content.  
- Strengthen **sports & long-form content** to attract diverse audiences.  

---

### 👥 User Demographics  
#### **Key Insights:**  
- **LioCinema has 4x more users** than JotStar, with a strong presence in **Tier 3 cities (43%)**.  
- JotStar dominates **Tier 1 cities (56%)**.  
- **Age Distribution:**  
  - LioCinema attracts **younger users (18-24 years)**.  
  - JotStar’s core audience is **25-44 years old**.  
- **Subscription Trends:**  
  - LioCinema’s free plan dominates, while **JotStar has balanced adoption of VIP, Premium, and Free plans**.  

#### **Recommendations:**  
- **Targeted cross-promotions**—Convert LioCinema’s free users to JotStar’s paid subscribers.  
- Expand **regional content** to attract LioCinema’s Tier 3 users.  
- Offer **tiered pricing & bundled plans** to cater to different age groups.  

---

### 🔄 Active vs. Inactive Users  
#### **Key Insights:**  
- **JotStar has higher engagement (85% active users)** vs. LioCinema (55%).  
- Younger users (18-24) are **most active on LioCinema**, while **25-34** is the most engaged group on JotStar.  
- **Plan-Based Activity:**  
  - LioCinema’s **free users are active**, but premium users show higher engagement.  
  - JotStar’s **VIP & Premium plans have 93% engagement**.  

#### **Recommendations:**  
- Use **JotStar’s engagement tactics** to **increase active users on LioCinema**.  
- Create **tier-based retention strategies** for different user segments.  
- Convert **LioCinema’s free users into paying subscribers** using JotStar’s engagement model.  

---

### ⏳ Watch Time Analysis  
#### **Key Insights:**  
- **JotStar users have significantly higher watch time** than LioCinema across all tiers.  
- **Tier 1 users** have the highest watch time on both platforms (JotStar: **131 hrs**, LioCinema: **35 hrs**).  
- **Device Trends:**  
  - Mobile is the dominant device.  
  - JotStar users spend **4x more time on mobile** than LioCinema users.  
  - **Higher TV & Laptop engagement** on JotStar.  

#### **Recommendations:**  
- **Implement engagement strategies** from JotStar to **increase watch time on LioCinema**.  
- Prioritize **mobile-first content** & optimize UI for better retention.  
- Promote **big-screen content** to enhance premium viewing experiences.  

---

### 📉 Downgrade Trends  
#### **Key Insights:**  
- **LioCinema’s downgrade rate is nearly double** JotStar’s (11.37% vs. 6.15%).  
- **Tier 1 users downgrade the most** on both platforms, with LioCinema seeing a sharper drop (16%).  
- **JotStar’s downgrade rate is increasing**, while LioCinema’s is improving.  

#### **Recommendations:**  
- Improve **content & engagement strategies** to **reduce downgrades**.  
- Investigate **JotStar’s rising downgrade rate** and introduce retention incentives.  
- Develop **personalized retention strategies** for different city tiers.  

---

### 📈 Upgrade Patterns  
#### **Key Insights:**  
- **JotStar has a much higher upgrade rate (9.74%) than LioCinema (1.13%)**.  
- **Upgrade Behavior:**  
  - LioCinema users move from **Free → Basic (50%)**.  
  - JotStar sees **VIP → Premium upgrades (65%)**.  
- **Tier 1 dominates LioCinema’s upgrades**, while **JotStar upgrades are highest in Tier 2**.  

#### **Recommendations:**  
- Improve **LioCinema’s Free-to-Premium conversion** strategies.  
- Investigate **JotStar’s declining upgrades** & introduce pricing/loyalty offers.  
- Optimize **city-tier-based monetization** based on upgrade trends.  

---

### 💰 Paid Users Distribution  
#### **Key Insights:**  
- **LioCinema has a higher free user base (57.3%)**, while **JotStar has a stronger premium mix**.  
- **Age Trends:**  
  - LioCinema’s **free plan dominates all age groups**.  
  - JotStar has a **balanced split between Free, VIP & Premium**.  

#### **Recommendations:**  
- Implement **targeted upselling strategies** to convert LioCinema’s free users.  
- Align **subscription models** post-merger to improve retention.  
- Introduce **city & age-based pricing** strategies.  

---

### 💸 Revenue Analysis  
#### **Key Insights:**  
- **JotStar leads in revenue (₹51.52M) vs. LioCinema (₹20.28M)**, but JotStar’s revenue is **declining**, while LioCinema’s is **growing**.  
- **City Contribution:**  
  - JotStar’s revenue is **Tier-1 driven (66%)**.  
  - LioCinema has stronger **Tier-2 traction (39%)**.  
- **Age Group Impact:**  
  - LioCinema’s **18-24 users contribute the most (40%)**.  
  - JotStar has a **balanced revenue split across age groups**.  

#### **Recommendations:**  
- **Leverage LioCinema’s growth momentum** to stabilize JotStar’s revenue decline.  
- Develop **tier-based monetization strategies** post-merger.  
- Expand **youth-focused premium offerings** on LioCinema.  

---

## 🏆 Strategic Growth & Market Positioning  
- **Boost engagement** through **regional content expansion** & AI-driven personalized recommendations.  
- **Gamification & rewards** to incentivize loyalty.  
- **OTT Bundles & Telecom Partnerships** to expand reach.  
- **AI-powered recommendations & multilingual UX** to improve retention.  
- **Strategic brand ambassadors** for mass appeal (e.g., **Shah Rukh Khan, Alia Bhatt, Bhuvan Bam, regional stars**).   

---
## ✅ Conclusion
This project provides critical insights into **LioCinema** and **Jotstar’s performance**, **subscriber behavior**, and **content trends**. The findings will help management **optimize content strategies** and **enhance user engagement** post-merger, positioning **Lio-Jotstar** as a dominant player in India's OTT market.

---
## 🛠️ Tools & Technologies
- **Power Query**: For data cleaning and transformation.
- **Power BI**: For interactive dashboard creation.
- **Canva**: For presenting insights to stakeholders.
- **Figma**: For dashbaord wireframing.
- [**Flaticon**](https://www.flaticon.com/): For icons
- [**Adobe Stock**](https://stock.adobe.com/in/) & [**shutterctock**](https://www.shutterstock.com/): For images

---
### **👨‍💻 Skills Demonstrated:**  
- Data Analysis  
- Visualization  
- Critical Thinking  
- Business Strategy  
- Communication  


