 Version	   |     Description
 ------------- | --------------
 1.1.8.29      |   Refactored to set "SSL factory" and "Hostname verifier" directly to each connection, instead of setting a global factory and verifier.
 1.1.6.20      |   Added ability to disable mobile network tests when a user uses a Wi-Fi network.
 1.1.5.14      |   Fixed ANR while atmospheric pressure measurements.
 1.1.3.18      |   Atmospheric Pressure measurements feature was implemented.
 1.0.12.6      |   WiFi measurements feature was implemented.
 1.0.8.7       |   Implemented collecting extra data.
 1.0.7.25      |   Resolved Insecure HostnameVerifier issue.
 1.0.6.8       |   Implemented writing to the file a errors logging if a device has no internet connection. Fixed a date sending to the server for devices which uses non arabic numbers.
 1.0.6.1       |   ​Implemented SDK-global error catching and logging system.
 1.0.5.31      |   Dropped Apache Httpclient lib usage in favour of custom code to mitigate a risk of conflicting references in partner app.
 1.0.5.24      |   ​Fixed​ crash in case when mobile network disappeared during the test starting.
 1.0.5.21      |   ​Fixed​ ​a disproportional volume of​ ​FailedMeasurement reports.
 1.0.5.18      |   Fixed crash in case of location permissions not granted.
 1.0.5.11      |   Dropped Gson lib usage in favour of custom code to mitigate a risk of conflicting references in partner app.
 1.0.5.3       |   First release of GDPR-compliant version of the SDK (deviceid, timestamp and location are never reported together, making it effectively impossible to trace measurements back to an individual)
 0.5.4.5       |   Use JobScheduler API for background tasks on devices with API level 21+ (this way background measurements don't count towards 'application wakeups')
