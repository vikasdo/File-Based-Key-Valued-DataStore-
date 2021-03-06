Built a file-Based Key-Value DataStore that supports the basic CRD(Create,read and delete) operations . 
This data store is meant to be used as a local storage for one single process on one laptop. The data store is exposed as a library
to the clients that can instantiate a class and work with the data store.

The data store will support the following functional requirements

1. It can be initialized using an optional file path. if one is not provided, it will reliably create itself in a resonable location on the laptop

2. A New Key Value pair can be added to the data store using the create operation. The key is always a string- capped at 32 chars. the value is always a JSON object - capped at 16KB

3. If Create is invoked from an existing key, an appropriate error must be returned.

4. A Read operation on a key can be performed by providing a key, and recieving the value in response as a JSON object 

5. A Delete operation can be performed by providing a key

6. Every Key supports setting a TIME TO LIVE property when it is created. This property is optional. if provided it will be evaluated as an integer defining the number of seconds 
   the key must be retained in the data store Once the TIME TO LIVE for a key has epired, the key will no longer be available for read or delete operation

7. Appropriate error messages must always be returned to a client if it uses the data store in unexpected ways or breached any limits


The data Store will also support the following non functional requirements 

1. The size of the file storing the data must never exceed 1GB

2. More than on Client process cannot be allowed to use the same file as a data store at any given time.

3. A client process is allowed to accedd the data store using multiple threads (if it desires to )
   the data must therefore be THREAD-SAFE

4. The client will bear as little memory costs as possible to use this data store while deriving maximum performance with respect to response times for accessing the data store