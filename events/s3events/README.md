# Overview

This package provides input types for Lambda functions that process Amazon S3 events.

# Sample Function

The following is a sample class and Lambda function that receives Amazon S3 event record data as an input and writes some of the record data to CloudWatch Logs. (Note that by default anything written to Console will be logged as CloudWatch Logs events.)

```go

import (
    "strings"
    "github.com/aws/aws-lambda-go/events/s3events")

func handler(ctx context.Context, s3Event s3events.S3Event) {
    for _, record := range s3Event.Records {
        s3 := record.S3
        fmt.Printf("[%s - %s] Bucket = %s, Key = %s \n", record.EventSource, record.EventTime, s3.Bucket.Name, s3.Object.Key) 
    }
}

```