# FinancialServicesCloud Objects(Last Updated: Winter '18)

## FSC Objects - Core Objects And Referral Management

* **Account** (Std. Object) -- Used to track Active or Inactive Clients, Prospects, Spouse, Partner, Dependents
  * Record Types 
    * Person Account
    * Individual
  * Individual Type (Internal Salesforce Read Only Field)
    * Individual
    * Group
    * "Blank" - This means its Business
* **Contact** (Std. Object) -- Represents information about an individual that pertains to their personhood, irrespective of relationship with your firm, such as Birthdate, TaxID number.
* **Lead** (Std. Object) -- Represents a lead associated with an individual. 
  * ExpressedInterest__c
    * Mortgage
    * Personal Loan
    * Credit Card
    * Savings Account
    * Checking Account
    * HELOC
    * Day to Day Banking
    * Manage Money
    * Property Purchase
    * Investments
    * Education
    * Manage Debt
  * ReferredByContact__c
    * External Contact who made the referral
  * ReferredByUser__c
    * Internal Salesforce User who made the referral.
* **Opportunity** (Std. Object) -- Represents an Opportunity associated with an Individual. 
  * ReferredByContact__c
    * External Contact who made the referral
  * ReferredByUser__c
    * Internal Salesforce User who made the referral
  * FinancialAccount__c
    * Indicates whether the billing Address is this Individual's Primary Address (TRUE) or not (FALSE)
* **User** (Std. Object) -- Represents a User in your Organization

## Features - Relationships & Roles

* **AccountAccountRelation** (Custom Object) -- Represents a relationship between two accounts, such as between a household and a business account.
  * Account__c 
  * Related_Account__c
  * InverseRelationship__c
    * Uniquely Identifies the relationship between Account and RelatedAccount, so that it can be referrenced by trigger that creates inverse relationship record.
* **AccountContactRelation** (Std. Object) -- Represents the relationship between **Individuals** (Specially the Contact Part of Individual) and the **Household(Account)** that the individual is a member of.
  * AccountContactRelation is a standard object that is available through the shared contact feature. 
  * AccountId - ID of the Household (account) that the individuals are member of.
  * ContactId - ID of the Contact, that partially represents individual.
  * IncludeInGroup__c - Include this account in a related Individual's Primary Group.
  * IsDirect - Indicates Account to Contact relationship is DIRECT, which means that it relates the account and contact parts of an individual to represent a single individual (TRUE). Otherwise, the relationship is INDIRECT, which means that it relates to.
* **ContactContactRelation** -- Represents the relationship between any two individuals.
  * Contact__c
  * RelatedContact__c
  * InverseRelationship__c
    * Uniquely Identifies the relationship between Contact and RelatedContact, so that it can be referrenced by trigger that creates inverse relationship record.
* **FinancialAccountRole** -- Represents the role occupied by the person or organization entity that is involved with a financial account, such as benificiary or trustee
  * RelatedAccount__c
    * Name of the Organization Entity that is involved with financial account.
  * RelatedContact__c
    * Name of the Person who is involved with financial account.
  * Role__c
    * Role descibes how the Organization Entity or Person is involved with the financial account
    * When the RecordType is set to "Account Role"
      * Corporation
      * Foundation
    * When the RecordType is set to "Contact Role"
      * Trustee
      * Beneficiary
      * Grantor
      * Accountant
      * Business Manager
* **ReciprocalRole** -- Represents the other entity's corresponding role in one-to-one relationships between entities.
  * CreateInverseRole__c
    * Indicates whether the corresponding reciprocal role record is created automatically for the inverse role(TRUE) or not(FALSE)
  * InverseRelationship__c
    * Uniquely identifies the relationship between Role and InverseRole__c so that it can be referenced by a trigger that creates the inverse relationship record
  * InverseRole__c
    * The role that the other entity occupies in the relationship, such as a grandparent to a grandchild, or an owned business to a proprietor.
  * RelationshipType__c
    * Type of entities involved in the relationship. Valid values:
      * All
      * Contact Contact Relation
      * Account Account Relation
    
## Features - Individual Information

* **Education** -- Represents an Individual's Education Background
* **Employment** -- Represents Information about an Individual's Employment History
* **IdentificationDocument** -- Represents Information about documents used to verify an individual Identity.
* **IdentityVerification** -- Represents Information about methods used to verify Clients Identity.
  * Verification Method
    * External
    * Last 4 Digits of ID
    * License
    * Manual
    * Mother's Maiden Name
* **LifeEvent** -- Represents the Client's Life Event such as Birthday or Marriage
  * EventType__c
    * College
    * New Baby
    * New Business
    * New Home
    * New Job
    * Retirement

## Features - Events & Tasks

* **Events** (Std. Object) -- Represents an Event associated with a client
* **Tasks** (Std. Object) -- Represents a Task associated with a client
   
## Features - External Alerts
  
* **Alert** -- Represents notification to alert advisors about client Accounts.

## Features - Financial Accounts

* **Financial Account** -- Represents a financial Account such as Investment Account, Bank Account or Insurance Policy
  * FinancialAccountTypes__c
    * 401 (a)
    * 401 (b)
    * 401 (k)
    * 529 Plan
    * Brokerage
    * Cash Management Account
    * CD
    * Checking
    * Credit Card
    * Discount Brokerage
    * Fixed Annuity
    * Individual Life
    * IRA
    * Mutual Fund
    * Profit Sharing
    * Rollover IRA
    * Roth IRA
    * Savings
    * Term Life
    * Variable Life
    * Whole Life
* **FinancialAccountTransaction** -- Represents Information about Single Financial Account Transaction
* **FinancialGoal** -- Represents Client's Financial Goal such as College Funds or Major Purchase
* **FinancialHoldings** -- Represents a financial holding in an investment account, such as shares of stock
  * AssetCategory
    * U.S Equity
    * Sector Equity
    * Allocation
    * International Equity
    * Alternative
    * Commodities
    * Taxable Bond
    * Municiple Bond
* **AssetsAndLiabilities** -- Represents Assets or Liabilities that are not present in a Client's Financial Accounts, such as real estate and collectibles.
  * AssetsAndLiabilitiesSource__c
    * Manual Entry
    * Yodlee
  * AssetsAndLiabilitiesType__c
    * Auto Loan
    * Mortgage
    * Other
    * Personal Loan
    * Real Estate
    * Equipment
    * Automobile
    * Collection
    * Gold
    * Jewelry
    * Cash
  * Ownership__c
    * Individual
    * Joint
    * Trust
* **Revenue** -- Represents data from Financial Services Cloud and External Systems to aggregate revenue streams for an advisor's book of business.
* **Securities** -- Represents a security such as stock or bond.
* **BillingStatements** -- Represents a Billing Statement for a Individual's Financial Account
* **Card** -- Represents Credit or Debit Card associated with this financial account. 
* **ChargeAndFees** -- Represents agreed-to fees and charge for servicing individual's financial accounts.

## Features - Action Plans

* **ActionPlan** -- Represents the instance of Action Plan, a set of tasks created from a Action Plan Template
* **ActionPlanItem** -- Represents the instance of ActionPlan Item
* **ActionPlanShare** -- Represents Share Entry on an action plan record.
* **ActionPlanTemplate** -- Represents Instance of Action Plan Template.
* **ActionPlanTemplateItem** -- Represents Instance of Action Plan Template Item.
* **ActionPlanTemplateItemValue** -- Represents Instance of Action Plan Template Item.
* **ActionPlanTemplateShare** -- Represents Share Entry on an Action Plan Template Record.
* **ActionPlanTemplateVersion** -- Represents Action Plan Template Version History.


## FSC Config Objects & Custom Metadata Objects

* **WealthAppConfig** -- Represents configuration information for Financial Services Cloud functionality
* **IndividualRecordTypeMapper** -- Maps a new custom Individual record type to the standard Individual record type from Financial Services Cloud.
* **GroupRecordTypeMapper** -- Maps a new custom Group record type to the standard Group record type from Financial Services Cloud.
* **ReferralRecordTypeMapper** -- Maps a new custom record type on the Lead object, used to represent a new type of referral, to the standard Referral record type from Financial Services Cloud.

