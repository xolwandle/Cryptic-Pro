### Task A — BTCZAR Market Summary

Request:
GET /v1/public/BTCZAR/marketsummary

Attached screenshot shows a successful response (200 OK) with live market data.

### Key Observations:
- currencyPair correctly returned as BTCZAR
- bidPrice (1282170) < askPrice (1282171) ✔
- lastTradedPrice is within bid/ask range ✔
- Response time ~90ms (good performance)

### Validation:
- Prices are positive ✔
- Market spread is logical ✔
- Data structure is consistent ✔

Conclusion:
The endpoint returns valid and consistent market data suitable for public consumption.

<img width="3024" height="1964" alt="image" src="https://github.com/user-attachments/assets/2faed41a-c958-47ff-b25f-2a466460d9cb" />


⚠️ Note: Values are dynamic and expected to change over time as market conditions update.



### Task B — Order Book Integrity Check

Request:
GET /v1/public/BTCZAR/orderbook

### Key Observations
- Response structure is valid
- Ask entries contain expected fields (side, quantity, price, currencyPair, orderCount)
- Visible ask prices are sorted in ascending order:

  1283053,
  1283054,
  1283249,
  1283314,
  1283351
  
- Checked spread consistency
- Prices and quantities are positive
- currencyPair is consistently BTCZAR

### Validations
- Sorting correct ✔
- No negative values ✔
- Spread logical ✔

### Potential Risk
- No checksum validation exposed

Conclusion:
The visible ask side of the order book appears valid and logically ordered. No anomalies were identified in the displayed sample. A full integrity check would also confirm bid ordering and spread validity.

<img width="3024" height="1964" alt="image" src="https://github.com/user-attachments/assets/46fe1037-ea72-466b-b0cc-859ea32758d7" />



### Task C - Currency Pair Validation

Request: 
GET /v1/public/pairs

### Key Observations
- Large dataset
- Consistent schema
- Includes trading status

### Validation
- No duplicate pairs ✔
- Proper formatting ✔

<img width="3024" height="1964" alt="image" src="https://github.com/user-attachments/assets/42c559f9-88a2-4028-bd4a-9d1062908a6a" />



