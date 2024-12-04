## Create a new bucket

```sh
aws s3api create-bucket --bucket acl-example-fh2 --region us-west-2
```

## Turn off Block Public Access for ACLs

```sh
aws s3api put-public-access-block \
--bucket acl-example-fh2 \
--public-access-block-configuration "BlockPublicAcls=false,IgnorePublicAcls=false,BlockPublicPolicy=true,RestrictPublicBuckets=true"
```

```sh
aws s3api get-public-access-block \
--bucket acl-example-fh2
```

## Change Bucket Ownership

```sh
aws s3api put-bucket-ownership-controls \
--bucket acl-example-fh2 \
--ownership-controls="Rules=[{ObjectOwnership=BucketOwnerPreferred}]"
```

## Change ACLs to allow for a user in another AWS Account

```sh
aws s3api put-bucket-acl \
--bucket acl-example-fh2 \
--access-control-policy file:///workspace/AWS-Examples/s3/acls/policy.json
```

## Access Bucket from other Account

```sh
touch example.txt
aws s3 cp example.txt s3://acl-example-fh2
aws s3 ls s3://acl-example-fh2
```

## Cleanup

```sh
aws rm s3 rm s3://acl-example-fh2/example.txt
aws rb s3 rb s3://acl-example-fh2
```