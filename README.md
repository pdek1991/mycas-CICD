# mycas-CICD
The system consists of five microservices:
● SMS-CAS Interface: This microservice accepts requests from SMS, which
sends REST API requests on different endpoints such as /generateosm,
/adddevice, /addentitlement, /removedevice, /removeentitlement,
and /removedevice. The SMS-CAS Interface takes these requests, saves
them in the database, and logs them into a log file. It then responds back
to SMS with an appropriate response.
● EMMG: This microservice is responsible for generating EMM based on
data received in the SMS-CAS Interface. The EMM data is then sent to
the Encryptor component.
● Encryptor: This microservice encrypts data in envelope encryption and
responds back to EMMG. The Encryptor must support 100 encryptions per
second.
● Cycler: This microservice takes encrypted EMM from the database and
carousels it based on some fixed configuration. The Cycler logs all the
data being carouselled.
● Scheduler: This microservice runs fixed tasks, such as changing keys
used for encryption and removing rows from the database for which expiry
has passed.

Interface/API Definitions
The SMS-CAS Interface exposes the following REST API endpoints:
● /generateosm: This endpoint generates an EMM for a given device.
● /adddevice: This endpoint adds a device to the system.
● /addentitlement: This endpoint adds an entitlement to a device.
● /removedevice: This endpoint removes a device from the system.
● /removeentitlement: This endpoint removes an entitlement from a
device.
● /removedevice: This endpoint removes a device from the system
