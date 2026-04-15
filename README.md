# Unofficial Banking API

This document provides a high-level, informational overview of how service interactions behave based on publicly observable system patterns.  
It is intended for educational purposes only and is not affiliated with any official provider.


---

## Example Endpoint

`POST /account-service/3000`

---

## Request Payload

```json
{
  "clientPubKey": "",
  "requestTime": "",
  "lang": "",
  "requestId": "",
  "encryptStr": {
    "clientId": "",
    "sessionId": "",
    "cifNo": "",
    "userName": ""
  },
  "device": {
    "deviceId": "",
    "os": "",
    "browser": "",
    "version": ""
  }
}
```

### Field Description

| Field | Type | Description |
|------|------|-------------|
| clientPubKey | string | Client public key used for encryption |
| requestTime | string | Timestamp of the request |
| lang | string | Language preference |
| requestId | string | Unique request identifier |
| encryptStr | object | Encrypted payload containing user/session data |
| device | object | Client device information |

#### encryptStr

| Field | Type | Description |
|------|------|-------------|
| clientId | string | Client identifier |
| sessionId | string | Session identifier |
| cifNo | string | Customer identifier |
| userName | string | Username |

#### device

| Field | Type | Description |
|------|------|-------------|
| deviceId | string | Unique device ID |
| os | string | Operating system |
| browser | string | Browser name |
| version | string | Application or browser version |

---

## Response

```json
{
  "responseId": "3000",
  "resCode": "00",
  "resTime": "",
  "encryptStr": {
    "listAccount": [
      {
        "accountNo": "",
        "branch": "",
        "balance": null,
        "availableBalance": null,
        "currency": "",
        "accountType": "",
        "accountTypeName": "",
        "productCode": "",
        "status": "",
        "openDate": "",
        "expireDate": null,
        "interestRate": null
      }
    ],
    "message": "Success",
    "traceId": ""
  },
  "msgCode": "INFO-00",
  "trace": "",
  "riskCode": "R0000"
}
```

### Response Fields

| Field | Type | Description |
|------|------|-------------|
| responseId | string | API response identifier |
| resCode | string | Result code ("00" indicates success) |
| resTime | string | Response timestamp |
| encryptStr | object | Encrypted response payload |
| msgCode | string | Message code |
| trace | string | Internal trace data |
| riskCode | string | Risk evaluation code |

#### encryptStr

| Field | Type | Description |
|------|------|-------------|
| listAccount | array | List of user accounts |
| message | string | Response message |
| traceId | string | Request trace identifier |

#### listAccount Item

| Field | Type | Description |
|------|------|-------------|
| accountNo | string | Account number |
| branch | string | Branch identifier |
| balance | number | Current balance |
| availableBalance | number | Available balance |
| currency | string | Currency code |
| accountType | string | Account type code |
| accountTypeName | string | Account type description |
| productCode | string | Product identifier |
| status | string | Account status |
| openDate | string | Account opening date |
| expireDate | string/null | Expiration date |
| interestRate | number/null | Interest rate |

---

## Notes

- All sensitive fields appear to be encapsulated within `encryptStr`.
- `resCode = "00"` indicates a successful operation.
- Null values may indicate non-applicable or unavailable data.
- Field naming suggests a structured, service-oriented backend design.

---

## Disclaimer

This document is based solely on externally observable behavior and inferred structure.  
It is not official documentation and should not be used for production or integration purposes.
