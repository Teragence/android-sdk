 Version	   |     Description
 ------------- | --------------
 1.0.5.3       |   First release of GDPR-compliant version of the SDK (deviceid, timestamp and location are never reported together, making it effectively impossible to trace measurements back to an individual)
 0.5.4.5       |   Use JobScheduler API for background tasks on devices with API level 21+ (this way background measurements don't count towards 'application wakeups')
