## Create a bucket

```sh
aws s3 mb s3://bucket-policy-example-fh2
```

## Create bucket policy

```sh
aws s3api put-bucket-policy --bucket bucket-policy-example-fh2 --policy file://policy.jsonn
```

## In the other account access the bucket

```sh
touch example.txt
aws s3 cp example.txt s3://bucket-policy-example-fh2
aws s3 ls s3://bucket-policy-example-fh2
```

## Cleanup

```sh
aws s3 rm s3://bucket-policy-example-fh2/example.txt
aws s3 rb s3://bucket-policy-example-fh2
```
