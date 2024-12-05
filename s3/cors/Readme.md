# Create website 1

## Create a bucket

```sh
aws s3 mb se:///cors-fun-fh2
```

## Change block public access

```sh
aws s3api put-public-access-block \
--bucket cors-fun-fh2 \
--public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=false,RestrictPublicBuckets=false"
```

## Create a bucket policy

```sh
aws s3api put-bucket-policy --bucket cors-fun-fh2 --policy file://bucket-policy.json
```

## Turn on static website hosting

```sh
aws s3api put-bucket-website --bucket cors-fun-fh2 --website-configuration file://website.json
```

## Upload index.html file and include a resource that would be cross-origin

```sh
aws s3 cp index.html s3://cors-fun-fh2
```

## view the website and see if the index.html is there.

http://cors-fun-fh2.s3-website-us-west-2.amazonaws.com
http://cors-fun-fh2.s3-website.us-west-2.amazonaws.com

# Create website 2

```sh
aws s3 mb s3://cors-fun2-fh2
```

## Change block public access

```sh
aws s3api put-public-access-block \
--bucket cors-fun2-fh2 \
--public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=false,RestrictPublicBuckets=false"
```

## Create a bucket policy

```sh
aws s3api put-bucket-policy --bucket cors-fun2-fh2 --policy file://bucket-policy2.json
```

## Turn on static website hosting

```sh
aws s3api put-bucket-website --bucket cors-fun2-fh2 --website-configuration file://website.json
```

## Upload the javascript file

```sh
aws s3 cp hello.js s3://cors-fun2-fh2
```

## Create API Gateway with mock response and then test the endpoint

```sh
curl -X POST -H "Content-Type: application/json" https://InsertInvokeIDHere.execute-api.us-west-2.amazonaws.com/prod/hello
```

## Set CORS on the bucket

aws s3api put-bucket-cors --bucket cors-fun-fh2 --cors-configuration file://cors.json
