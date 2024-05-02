# How to host a zarr-based source data on EWC (European Weather Cloud)

First you will neet to [get an account](https://confluence.ecmwf.int/display/EWCLOUDKB/Getting+access+to+EWC). You will have to choose either a EUMETSAT or ECMWF tenancy (drawbacks/benefits between the two?). You will receive S3 credentials (I, Leif, did anyway).


## 1. Create bucket


### Using the command line

- [examples using s3cmd](https://confluence.ecmwf.int/display/EWCLOUDKB/Object+storage%3A+How+to+use+s3cmd+and+s3fs)

```bash
lcd@wrk1:/dmidata/projects/cloudphysics/danra/data$ s3cmd mb s3://danra
Bucket 's3://danra/' created
```

```bash
lcd@wrk1:/dmidata/projects/cloudphysics/danra/data$ s3cmd info s3://danra
s3://danra/ (bucket):
   Location:  default
   Payer:     BucketOwner
   Ownership: none
   Versioning:none
   Expiration rule: none
   Block Public Access: none
   Policy:    none
   CORS:      none
   ACL:       *anon*: READ
   ACL:       cci1-ewcloud-ecmwf-ml-pilot: FULL_CONTROL
   URL:       http://object-store.os-api.cci1.ecmwf.int/danra/
```

### Using the web interface

2. Log in to the [Morpheus webportal](https://confluence.ecmwf.int/display/EWCLOUDKB/Logging+in+to+Morpheus) using the tenancy you have been given (ECMWF or EUMETSAT)

3. [Create a bucket in the S3 object store](https://confluence.ecmwf.int/display/EWCLOUDKB/How+to+create+S3+buckets+in+Morpheus) of the tenancy you have been given.



## 2. Upload files


Single file:

```bash
(base) lcd@wrk1:/dmidata/projects/cloudphysics/danra/data$ s3cmd put CHANGELOG.md s3://danra/
upload: 'CHANGELOG.md' -> 's3://danra/CHANGELOG.md'  [1 of 1]
 1060 of 1060   100% in    0s    12.35 KB/s  done
```


Directory:


```bash
(base) lcd@wrk1:/dmidata/projects/cloudphysics/danra/data$ s3cmd sync v0.2.2/ s3://danra/v0.2.2/ --debug
```

Note: trailing slashes are required, s3cmd does at lot of checks before uploading which is why I include `--debug` to see what is happening

