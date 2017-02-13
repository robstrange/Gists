### Step 1 - Create read role
- The aim of this user is to allow them to read all fields in a document that are relevant to them

`POST /_xpack/security/role/CustomerA-read-role
{
  "indices": [
    {
      "names": [ "device-test" ],
      "privileges": [ "read" ],
      "query" : {\”match\”: {\”Customer\”: \”CustomerA\”}}”
    }
  ]
}`

### Step 2 - Setup Overview role
- The aim of the role is to allow a member of the team to see some fields from all documents

`POST /_xpack/security/role/public-info-role
{
  "indices": [
    {
      "names": [ "device-test" ],
      "privileges": [ "read" ],
      "field_security" : {
        "grant" : [ "Customer", "DeviceName"]
      }
    }
  ]
}`

### Step 3 - Setup User

`POST /_xpack/security/user/CustomerA-reader
{
  "password" : "demodemo",
  "roles" : [ "CustomerA-read-role", "public-info-role" ],
  "full_name" : "CustomerA Reader",
  "email" : "a@a.a",
  "enabled": true
}`

### Step 4 - Post Docs

`PUT device-test/device/1
{
    "DeviceName" : "CustomerA-fw-01",
    "Serial" : "abcd-1111-efgh",
    "Customer" : "CustomerA",
    "IPAddress" : "10.10.10.1"
}`

`PUT device-test/device/2
{
    "DeviceName" : "CustomerB-fw-01",
    "Serial" : "abcd-3333-efgh",
    "Customer" : "CustomerB",
    "IPAddress" : "20.10.10.1"
}`

When logging in as `CustomerA-reader` you should be able to see
- All documents but only fields `DeviceName` and `Customer`
- All the fields in all documents where `Customer:CustomerA`
