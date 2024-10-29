---
editable: false
sourcePath: en/_api-ref-grpc/dataproc/v1/api-ref/grpc/Job/get.md
---

# Data Proc API, gRPC: JobService.Get {#Get}

Returns the specified job.

## gRPC request

**rpc Get ([GetJobRequest](#yandex.cloud.dataproc.v1.GetJobRequest)) returns ([Job](#yandex.cloud.dataproc.v1.Job))**

## GetJobRequest {#yandex.cloud.dataproc.v1.GetJobRequest}

```json
{
  "clusterId": "string",
  "jobId": "string"
}
```

#|
||Field | Description ||
|| clusterId | **string**

Required field. ID of the cluster to request a job from. ||
|| jobId | **string**

Required field. ID of the job to return.

To get a job ID make a [JobService.List](/docs/data-proc/api-ref/grpc/Job/list#List) request. ||
|#

## Job {#yandex.cloud.dataproc.v1.Job}

```json
{
  "id": "string",
  "clusterId": "string",
  "createdAt": "google.protobuf.Timestamp",
  "startedAt": "google.protobuf.Timestamp",
  "finishedAt": "google.protobuf.Timestamp",
  "name": "string",
  "createdBy": "string",
  "status": "Status",
  // Includes only one of the fields `mapreduceJob`, `sparkJob`, `pysparkJob`, `hiveJob`
  "mapreduceJob": {
    "args": [
      "string"
    ],
    "jarFileUris": [
      "string"
    ],
    "fileUris": [
      "string"
    ],
    "archiveUris": [
      "string"
    ],
    "properties": "string",
    // Includes only one of the fields `mainJarFileUri`, `mainClass`
    "mainJarFileUri": "string",
    "mainClass": "string"
    // end of the list of possible fields
  },
  "sparkJob": {
    "args": [
      "string"
    ],
    "jarFileUris": [
      "string"
    ],
    "fileUris": [
      "string"
    ],
    "archiveUris": [
      "string"
    ],
    "properties": "string",
    "mainJarFileUri": "string",
    "mainClass": "string",
    "packages": [
      "string"
    ],
    "repositories": [
      "string"
    ],
    "excludePackages": [
      "string"
    ]
  },
  "pysparkJob": {
    "args": [
      "string"
    ],
    "jarFileUris": [
      "string"
    ],
    "fileUris": [
      "string"
    ],
    "archiveUris": [
      "string"
    ],
    "properties": "string",
    "mainPythonFileUri": "string",
    "pythonFileUris": [
      "string"
    ],
    "packages": [
      "string"
    ],
    "repositories": [
      "string"
    ],
    "excludePackages": [
      "string"
    ]
  },
  "hiveJob": {
    "properties": "string",
    "continueOnFailure": "bool",
    "scriptVariables": "string",
    "jarFileUris": [
      "string"
    ],
    // Includes only one of the fields `queryFileUri`, `queryList`
    "queryFileUri": "string",
    "queryList": {
      "queries": [
        "string"
      ]
    }
    // end of the list of possible fields
  },
  // end of the list of possible fields
  "applicationInfo": {
    "id": "string",
    "applicationAttempts": [
      {
        "id": "string",
        "amContainerId": "string"
      }
    ]
  }
}
```

A Data Proc job. For details about the concept, see [documentation](/docs/data-proc/concepts/jobs).

#|
||Field | Description ||
|| id | **string**

ID of the job. Generated at creation time. ||
|| clusterId | **string**

ID of the Data Proc cluster that the job belongs to. ||
|| createdAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp. ||
|| startedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

The time when the job was started. ||
|| finishedAt | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

The time when the job was finished. ||
|| name | **string**

Name of the job, specified in the [JobService.Create](/docs/data-proc/api-ref/grpc/Job/create#Create) request. ||
|| createdBy | **string**

The id of the user who created the job ||
|| status | enum **Status**

Job status.

- `STATUS_UNSPECIFIED`
- `PROVISIONING`: Job is logged in the database and is waiting for the agent to run it.
- `PENDING`: Job is acquired by the agent and is in the queue for execution.
- `RUNNING`: Job is being run in the cluster.
- `ERROR`: Job failed to finish the run properly.
- `DONE`: Job is finished.
- `CANCELLED`: Job is cancelled.
- `CANCELLING`: Job is waiting for cancellation. ||
|| mapreduceJob | **[MapreduceJob](#yandex.cloud.dataproc.v1.MapreduceJob)**

Specification for a MapReduce job.

Includes only one of the fields `mapreduceJob`, `sparkJob`, `pysparkJob`, `hiveJob`.

Specification for the job. ||
|| sparkJob | **[SparkJob](#yandex.cloud.dataproc.v1.SparkJob)**

Specification for a Spark job.

Includes only one of the fields `mapreduceJob`, `sparkJob`, `pysparkJob`, `hiveJob`.

Specification for the job. ||
|| pysparkJob | **[PysparkJob](#yandex.cloud.dataproc.v1.PysparkJob)**

Specification for a PySpark job.

Includes only one of the fields `mapreduceJob`, `sparkJob`, `pysparkJob`, `hiveJob`.

Specification for the job. ||
|| hiveJob | **[HiveJob](#yandex.cloud.dataproc.v1.HiveJob)**

Specification for a Hive job.

Includes only one of the fields `mapreduceJob`, `sparkJob`, `pysparkJob`, `hiveJob`.

Specification for the job. ||
|| applicationInfo | **[ApplicationInfo](#yandex.cloud.dataproc.v1.ApplicationInfo)**

Attributes of YARN application. ||
|#

## MapreduceJob {#yandex.cloud.dataproc.v1.MapreduceJob}

#|
||Field | Description ||
|| args[] | **string**

Optional arguments to pass to the driver. ||
|| jarFileUris[] | **string**

JAR file URIs to add to CLASSPATH of the Data Proc driver and each task. ||
|| fileUris[] | **string**

URIs of resource files to be copied to the working directory of Data Proc drivers
and distributed Hadoop tasks. ||
|| archiveUris[] | **string**

URIs of archives to be extracted to the working directory of Data Proc drivers and tasks. ||
|| properties | **string**

Property names and values, used to configure Data Proc and MapReduce. ||
|| mainJarFileUri | **string**

HCFS URI of the .jar file containing the driver class.

Includes only one of the fields `mainJarFileUri`, `mainClass`. ||
|| mainClass | **string**

The name of the driver class.

Includes only one of the fields `mainJarFileUri`, `mainClass`. ||
|#

## SparkJob {#yandex.cloud.dataproc.v1.SparkJob}

#|
||Field | Description ||
|| args[] | **string**

Optional arguments to pass to the driver. ||
|| jarFileUris[] | **string**

JAR file URIs to add to CLASSPATH of the Data Proc driver and each task. ||
|| fileUris[] | **string**

URIs of resource files to be copied to the working directory of Data Proc drivers
and distributed Hadoop tasks. ||
|| archiveUris[] | **string**

URIs of archives to be extracted to the working directory of Data Proc drivers and tasks. ||
|| properties | **string**

Property names and values, used to configure Data Proc and Spark. ||
|| mainJarFileUri | **string**

The HCFS URI of the JAR file containing the `main` class for the job. ||
|| mainClass | **string**

The name of the driver class. ||
|| packages[] | **string**

List of maven coordinates of jars to include on the driver and executor classpaths. ||
|| repositories[] | **string**

List of additional remote repositories to search for the maven coordinates given with --packages. ||
|| excludePackages[] | **string**

List of groupId:artifactId, to exclude while resolving the dependencies provided in --packages to avoid dependency conflicts. ||
|#

## PysparkJob {#yandex.cloud.dataproc.v1.PysparkJob}

#|
||Field | Description ||
|| args[] | **string**

Optional arguments to pass to the driver. ||
|| jarFileUris[] | **string**

JAR file URIs to add to CLASSPATH of the Data Proc driver and each task. ||
|| fileUris[] | **string**

URIs of resource files to be copied to the working directory of Data Proc drivers
and distributed Hadoop tasks. ||
|| archiveUris[] | **string**

URIs of archives to be extracted to the working directory of Data Proc drivers and tasks. ||
|| properties | **string**

Property names and values, used to configure Data Proc and PySpark. ||
|| mainPythonFileUri | **string**

URI of the file with the driver code. Must be a .py file. ||
|| pythonFileUris[] | **string**

URIs of Python files to pass to the PySpark framework. ||
|| packages[] | **string**

List of maven coordinates of jars to include on the driver and executor classpaths. ||
|| repositories[] | **string**

List of additional remote repositories to search for the maven coordinates given with --packages. ||
|| excludePackages[] | **string**

List of groupId:artifactId, to exclude while resolving the dependencies provided in --packages to avoid dependency conflicts. ||
|#

## HiveJob {#yandex.cloud.dataproc.v1.HiveJob}

#|
||Field | Description ||
|| properties | **string**

Property names and values, used to configure Data Proc and Hive. ||
|| continueOnFailure | **bool**

Flag indicating whether a job should continue to run if a query fails. ||
|| scriptVariables | **string**

Query variables and their values. ||
|| jarFileUris[] | **string**

JAR file URIs to add to CLASSPATH of the Hive driver and each task. ||
|| queryFileUri | **string**

URI of the script with all the necessary Hive queries.

Includes only one of the fields `queryFileUri`, `queryList`. ||
|| queryList | **[QueryList](#yandex.cloud.dataproc.v1.QueryList)**

List of Hive queries to be used in the job.

Includes only one of the fields `queryFileUri`, `queryList`. ||
|#

## QueryList {#yandex.cloud.dataproc.v1.QueryList}

#|
||Field | Description ||
|| queries[] | **string**

List of Hive queries. ||
|#

## ApplicationInfo {#yandex.cloud.dataproc.v1.ApplicationInfo}

#|
||Field | Description ||
|| id | **string**

ID of YARN application ||
|| applicationAttempts[] | **[ApplicationAttempt](#yandex.cloud.dataproc.v1.ApplicationAttempt)**

YARN application attempts ||
|#

## ApplicationAttempt {#yandex.cloud.dataproc.v1.ApplicationAttempt}

#|
||Field | Description ||
|| id | **string**

ID of YARN application attempt ||
|| amContainerId | **string**

ID of YARN Application Master container ||
|#