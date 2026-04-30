## Task D - Negative API test cases

### Invalid Pair
GET /v1/public/INVALID/marketsummary

Expected: Error  
Actual: Error ✔

<img width="3024" height="1964" alt="image" src="https://github.com/user-attachments/assets/c6e1fe7c-0e20-4b10-9bba-1cb6f42044a8" />

### Wrong Method
POST /v1/public/pairs

Expected:
Request should be rejected because the endpoint is intended for GET access only.

Actual:
404 Not Found ✔

Interpretation:
The API rejected the unsupported method by not matching a POST route for this resource.
This is still acceptable negative-path behaviour, although a 405 Method Not Allowed
would have been a more explicit REST response.

<img width="3024" height="1964" alt="image" src="https://github.com/user-attachments/assets/ae2b6c5c-366b-4376-976e-16d209f87668" />


### Attempted Missing Path Test
GET /v1/public//marketsummary

Expected:
Request might fail due to an invalid path structure.

Actual:
No error observed.

Interpretation:
This is likely due to path normalization by the server or gateway, where a double slash
is collapsed before route matching. Because of that, this is not a reliable negative test
for this API.

<img width="3024" height="1964" alt="image" src="https://github.com/user-attachments/assets/e7e5311a-c06a-4d9c-bab1-842ec6836936" />

## Task E - Authentication & Security Boundary Testing

### Approach
I tested private endpoints without valid authentication in order to verify that the API
correctly blocks unauthenticated access and does not expose private data.

I used the following variations:
- no authentication headers
- missing headers
- malformed or invalid authentication values
- incorrect HTTP method on a private endpoint

### Endpoint: /v1/account/balances

### Without Auth
Response: 403 Forbidden ✔

<img width="3024" height="1964" alt="image" src="https://github.com/user-attachments/assets/0ba39a59-4eac-4aae-bc77-040dabd01681" />

---

### Endpoint: /v1/orders/market

### GET instead of POST
Response: 403 Forbidden ✔

<img width="3024" height="1964" alt="image" src="https://github.com/user-attachments/assets/8bef3733-7d2b-424a-aca8-33c4e147815d" />

---

### Endpoint: /v1/orders/open

### Invalid Signature
Response: 403 Forbidden ✔

<img width="3024" height="1964" alt="image" src="https://github.com/user-attachments/assets/4824aca9-902c-4ddf-a691-83f338dc1789" />

---

### Endpoint: /v1/wallet/crypto/addresses/BTCZAR
Response: 403 Forbidden ✔

<img width="3024" height="1964" alt="image" src="https://github.com/user-attachments/assets/1c8f6116-404a-431e-a4a9-3f1478c5264d" />


## Security Findings

### ✅ Positive
- Proper rejection of unauthenticated requests
- Correct HTTP status usage
- No sensitive data leakage

### ⚠️ Potential Concerns
- No visible rate limiting feedback
- Error messages could reveal structure (if too verbose)

---

## Conclusion
Authentication boundary is well enforced.
No major security flaws observed in basic probing.
