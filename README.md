# Transaction-fraud-detection
Some ideas and sum-ups from Kaggle competition.

  1. Data loading
  2. Inside the data:
    - Transaction table

   TransactionDT: timedelta from a given reference datetime (not an actual timestamp)
  “TransactionDT first value is 86400, which corresponds to the number of seconds in a day (60 * 60 * 24 = 86400) so I think the unit is seconds. Using this, we know the data spans 6 months, as the maximum value is 15811131, which would correspond to day 183.”

   TransactionAMT: transaction payment amount in USD
    “Some of the transaction amounts have three decimal places to the right of the decimal point. There seems to be a link to three decimal places and a blank addr1 and addr2 field. Is it possible that these are foreign transactions and that, for example, the 75.887 in row 12 is the result of multiplying a foreign currency amount by an exchange rate?”

   ProductCD: product code, the product for each transaction
    “Product isn't necessary to be a real 'product' (like one item to be added to the shopping cart). It could be any kind of service.”

   card1 - card6: payment card information, such as card type, card category, issue bank, country, etc.

   addr: address
   “both addresses are for purchaser
    addr1 as billing region
    addr2 as billing country”
    
   dist: distance
    "distances between (not limited) billing address, mailing address, zip code, IP address, phone area, etc.”
   
   P_ and (R_) emaildomain: purchaser and recipient email domain “ certain transactions don't need recipient, so Remaildomain is null.”
    
   C1-C14: counting, such as how many addresses are found to be associated with the payment card, etc. The actual meaning is masked.
    
   D1-D15: timedelta, such as days between previous transaction, etc.
   
   M1-M9: match, such as names on card and address, etc.
   
   Vxxx: Vesta engineered rich features, including ranking, counting, and other entity relations.
   “For example, how many times the payment card associated with a IP and email or address appeared in 24 hours time range, etc.”
    
   "All Vesta features were derived as numerical. some of them are count of orders within a clustering, a time-period or condition, so the value is finite and has ordering (or ranking). I wouldn't recommend to treat any of them as categorical. If any of them resulted in binary by chance, it maybe worth trying."

