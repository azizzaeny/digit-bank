
**Design Domain Entity**
all attribute of entity use namespaces of their parent entity

```
customer/id  index
customer/full-name
customer/emails []
customer/phones []
customer/identity-number
customer/national-tax-identity 
customer/created-at
customer/status 


auth/customer-id 
auth/primary-email index unique
auth/primary-phones index unique 
auth/type [phones, email, soa] 
auth/password
auth/reset-token


accounts/customer-id 
accounts/account-id index 
accounts/balance
accounts/currency
accounts/limit-withdrawal
accounts/limit-single-transactions


ledger/ledger-id index 
ledger/account-id 
ledger/statement-type [credit debit]
ledger/timestamp


cards/account-id
cards/card-id  index unique 
cards/credit-limit
cards/status
cards/type [yellow,blue,red]


transactions/id
transactions/account-id
transactions/amounts
transactions/currencies
transaction/types


transaction-fees/charges
transaction-fees/transaction-id 
```

Customer will have multiple email and phone number as their secondary reserve. when authenticating they used their primary ones. they can set their authentication methods using phone-number or emails.  

Passwords stored as bcrypt encripytions, and only reverse matching not re-encode back to the original values.  


Customer sign up for the accounts will have multiple accounts with given currencies, when he join up he can request of credits cards. with given basic approved card limit. later on it will be increased as of customer rewards and level reach premium users. the rewards or customer level is determined by how much average balance they have monthly.  


The customer level also determine how much transactions fees they pay each transactions occur. for basic customer level transaction fees set to 5k in range of bellow amounts 1M deposit accounts. set to 2.5k when customer have more than 1M and bellow 10M in their balance each month. set to 1k when customer have more than 10M balances.  


There are two type transaction entity exists general banking activity and credit cards payments. cards -> into transactions entity. accounts -> into ledger entity.  

Each movements of accounts transaction saved in the balanced ledger entity between debit and credit. this will create a bank statement(later)  

When customer blocks his credit cards, their must include reason and metadata. we will use metadata a lot. metadata as third party partner merchant will stored in metadata.  


Transaction will processed asynchronously and inflight payment and projected balances will come in vary.   

As for account limits, we set it default to dialy limit withdrawal of 100M and single transaction in 100M, we are not separating user setting and bank setting.  

Each transaction will accompany with transaction token not only credential token headers. transaction token live shortly in 1 time transaction. the will be vary such us otp password and pin.  

user can determine how much transaction amounts is needed in order to use transaction token.






