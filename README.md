# Priority1py
Priority1 API library

# Getting Started
The easiest way to get started is to follow the below example:

```
from Priority1py import Priority1py as p1
from Priority1py import Details, IDType

if __name__ == '__main__':
    priority1 = p1.Priority1py('your-priority1-api-key')
```

Once the Priority1py object is created, getting any details is easy!

``` 
    # get the BOL number for a shipment
    bol = priority1.get_identifier('shipmentPO', IDType.PO, IDType.BOL)

    # get the current status
    status = priority1.get_shipment_details('shipmentPO', IDType.PO, Details.STATUS)

    # get the latest tracking
    track = priority1.get_latest_tracking('shipmentPO', IDType.PO)
```

The user should pass in the enums instead of custom strings in order to prevent any
incorrect strings being passed to the API on the backend.

# Object Functions
The following functions are to be called by the Priority1py object instance.

## Common arguments
These two arguments are passed in to all functions.
```
identifier : the shipment identifier of user's choice
identifiertype : the type of the identifier
    This argument accepts on those listed in Priority1py.IDType
```

## get_full_tracking(identifier, identifiertype)
### Arguments 
See above.
### Return
Returns a json list of all the tracking data available for the shipment.
### Exceptions
Raises an exception if no shipment was found with the given identifier.

## get_latest_tracking(identifier, identifiertype)
### Arguments
See above.
### Return
Returns the json of the latest tracking update available.
### Exceptions 
Raises an exception if no shipment was found with the given identifier.

## get_shipment_details(identifier, identifiertype, target)
### Arguments
```
target : the desired detail of the given shipment
```
Valid details :
```
IDType.CARRIER
IDType.CARRIER_CODE
IDType.STATUS
```
### Return
Returns a string of the desired detail

## get_shipment_details(identifier, identifiertype, target)
### Arguments
```
target : the desired identifier for the passed shipment.
```
### Return
Returns the string of the desired identifier





