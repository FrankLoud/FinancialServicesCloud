# FinancialServicesCloud

### FSC Objects - Core

* **Account** -- Used to track Active or Inactive Clients, Prospects, Spouse, Partner, Dependents
  * Record Types 
    * Person Account
    * Individual
  * Individual Type (Internal Salesforce Read Only Field)
    * Individual
    * Group
    * "Blank" - This means its Business

* **AccountAccountRelation** -- Represents a relationship between two accounts, such as between a household and a business account.
  * Account__c & Related_Account__c 
    * Tracks account and its related account
  * InverseRelationship__c
    * Uniquely Identifies the relationship between Account and RelatedAccount, so that it can be referrenced by trigger that creates inverse relationship record.
    
* **AccountContactRelation** -- Represents the relationship between **individuals** (Specially the Contact Part of Individual) and the **Household(Account)** that the individual is a member of.

#### Features - Action Plans
* **ActionPlan** -- Represents the instance of Action Plan, a set of tasks created from a Action Plan Template
* **ActionPlanItem** -- Represents the instance of ActionPlan Item
* **ActionPlanShare** -- Represents Share Entry on an action plan record.
* **ActionPlanTemplate** -- Represents Instance of Action Plan Template.
* **ActionPlanTemplateItem** -- Represents Instance of Action Plan Template Item.
* **ActionPlanTemplateItemValue** -- Represents Instance of Action Plan Template Item.
* **ActionPlanTemplateShare** - Represents Share Entry on an Action Plan Template Record.
* **ActionPlanTemplateVersion**
