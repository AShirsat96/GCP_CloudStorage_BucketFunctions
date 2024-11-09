# Google Cloud Storage Operations

A Python implementation for managing Google Cloud Storage buckets. This utility provides functions for creating, listing, and deleting buckets in Google Cloud Storage.

## Prerequisites

- Python 3.8.19
- Google Cloud Platform Account
- Project ID
- Configured Google Cloud credentials

## Installation

Install the required Google Cloud libraries:

```bash
pip install google-cloud-storage
pip install google-auth google-auth-application-default
```

## Required Libraries
```python
import os
import os.path
import sys
import venv
from google.cloud import storage
```

## Authentication

The script uses Application Default Credentials (ADC) for authentication:

```python
def authenticate_implicit_with_adc(project_id="your-project-id"):
    """
    Authenticates with Google Cloud using Application Default Credentials.
    
    Args:
        project_id (str): The project id of your Google Cloud project.
    """
    storage_client = storage.Client(project=project_id)
    buckets = storage_client.list_buckets()
```

## Features

### 1. Create Bucket
Creates a new bucket in Google Cloud Storage with specified configurations.

```python
def create_bucket_CloudStorage(bucket_name):
    """
    Creates a new bucket in the Asia Southeast region with standard storage class.
    
    Args:
        bucket_name (str): Name for the new bucket
        
    Returns:
        google.cloud.storage.bucket.Bucket: The created bucket object
    """
```

Example usage:
```python
new_bucket = create_bucket_CloudStorage('your-bucket-name')
```

Configuration details:
- Region: asia-southeast1
- Storage Class: STANDARD

### 2. List Buckets
Lists all buckets in your Google Cloud Storage project.

```python
def list_buckets_CloudStorage():
    """
    Lists all buckets in the project.
    
    Handles exceptions and ensures proper client closure.
    """
```

Example usage:
```python
list_buckets_CloudStorage()
```

### 3. Delete Bucket
Deletes a specified bucket from Google Cloud Storage.

```python
def delete_bucket_CloudStorage(bucket_name):
    """
    Deletes a specified bucket.
    
    Args:
        bucket_name (str): Name of the bucket to delete
    """
```

Example usage:
```python
delete_bucket_CloudStorage("bucket-to-delete")
```

## Error Handling

The implementation includes:
- Exception handling for bucket operations
- Proper client closure in finally blocks
- Error reporting for failed operations

## Client Initialization

```python
project_id = "your-project-id"
storage_client = storage.Client(project=project_id)
```

## Best Practices

1. Authentication:
   - Use Application Default Credentials
   - Keep credentials secure
   - Never commit credentials to version control

2. Resource Management:
   - Close storage client after use
   - Handle exceptions appropriately
   - Validate bucket names before operations

3. Storage Classes:
   - Use appropriate storage class based on needs
   - STANDARD is used by default

4. Regional Configuration:
   - Default region is set to asia-southeast1
   - Modify region based on your requirements

## Example Workflow

```python
# Initialize
project_id = "your-project-id"
authenticate_implicit_with_adc(project_id)
storage_client = storage.Client(project=project_id)

# Create bucket
new_bucket = create_bucket_CloudStorage("new-bucket-name")

# List all buckets
list_buckets_CloudStorage()

# Delete bucket
delete_bucket_CloudStorage("bucket-to-delete")
```
