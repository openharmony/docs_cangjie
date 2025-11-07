# Time and Timezone Service Error Codes

## -1 Time and Timezone Service Exception

**Error Message**

  The parameter check failed or permission denied or system error.

**Error Description**

Parameter validation failed, permission verification failed, or time and timezone service exception.

**Possible Causes**

This error code represents a generic error code. The specific exception can be determined based on the error message. Possible causes include:

1. Parameter validation failed - invalid parameters were passed.
2. Permission verification failed - permissions are not configured. The application setting time requires ohos.permission.SET_TIME or setting the timezone requires ohos.permission.SET_TIME_ZONE.
3. System runtime exception - kernel generic errors such as memory allocation or multi-thread processing failures.

**Resolution Steps**

1. For parameter validation failures: Check whether parameters are passed as required.
2. For permission verification failures: Configure ohos.permission.SET_TIME for application time settings or ohos.permission.SET_TIME_ZONE for timezone settings.
3. For system runtime exceptions: Verify whether sufficient memory is available.