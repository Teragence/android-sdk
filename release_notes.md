 Version	   |     Description
 ------------- | --------------
 1.0.5.24      |   ​Fixed​ crash in case when mobile network disappeared during the test starting.
 1.0.5.21      |   ​Fixed​ ​a disproportional volume of​ ​FailedMeasurement reports.
 1.0.5.18      |   Fixed crash in case of location permissions not granted.
 1.0.5.11      |   Dropped Gson lib usage in favour of custom code to mitigate a risk of conflicting references in partner app.
 1.0.5.3       |   First release of GDPR-compliant version of the SDK (deviceid, timestamp and location are never reported together, making it effectively impossible to trace measurements back to an individual)
 0.5.4.5       |   Use JobScheduler API for background tasks on devices with API level 21+ (this way background measurements don't count towards 'application wakeups')
