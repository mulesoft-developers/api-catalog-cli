# Shipping API - UAPIM Demo

## Note: this is a fake documentation

Show a single shipping order if current User has access permissions to it.

**URL** : `/api/shipping/:pk/`

**URL Parameters** : `pk=[integer]` where `pk` is the ID of the Ship on the
server.

**Method** : `GET`

**Auth required** : YES

**Permissions required** :

User is at least one of the following in relation to the Ship requested:

* Owner `OO`
* Admin `AA`
* Viewer `VV`

**Data**: `{}`

## Success Response

**Condition** : If Pet exists and Authorized User has required permissions.

**Code** : `200 OK`

**Content example**

```json
{
    "id": 345,
    "name": "Super Pet",
    "enterprise": false,
    "url": "http://testserver/api/Pets/345/"
}
```

## Error Responses

**Condition** : If Pet does not exist with `id` of provided `pk` parameter.

**Code** : `404 NOT FOUND`

**Content** : `{}`

### Or

**Condition** : If Pet exists but Authorized User does not have required
permissions.

**Code** : `403 FORBIDDEN`

**NOTEBOOKS**

```notebook
// Authenticate client
API.authenticate(myclient);
```

```notebook 
//fetch info
fetch('https://anypoint.mulesoft.com/exchange/api/v1/health').then((res) => res.json())
```

**Content** :

```json
{"detail": "You do not have permission to perform this action."}
```

## Notes

There are security issues:

* This view allows existing users to test for existence of Pets that exist
    but that they do not have access to.
* Pet IDs are sequential so an authorized user can count all the Pets
    on the system.
