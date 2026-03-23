# GCLOUD - Commands

## Revoking all logins
```
gcloud auth revoke --all
```

## Revoking specific login
```
gcloud auth revoke <email>
```

gcloud auth revoke

## Initializing `gcloud`

To initialize gcloud you need to choose or log into an account. Once logged you don't need to do that again.
```
git init
```

 - Type 1 > ENTER
 - Type y > ENTER
 - Wait login page load
 - Click on your account
 - Click on Next
 - Click on Allow

### Adding more accounts
```
gcloud auth login
```
or
```
git init
```

 - Type 1 > ENTER
 - Choose "Sign in with a new Google Account"
 - Wait login page load
 - Click on your account
 - Click on Next
 - Click on Allow
---


To see logged account:
```
gcloud auth list
```

---
## Setting a project

Se all projects
```
gcloud projects list
gcloud config set project <PROJECT ID>
```

# List of commands to take

```
gcloud compute disks list
gcloud compute disks describe disk-1 --zone=us-central1-a
gcloud compute disks delete disk-1 --zone=us-central1-a
gcloud compute snapshots create snap-disk-1 --source-disk=disk-1 --source-disk-zone=us-central1-a
gcloud compute snapshots list
```

