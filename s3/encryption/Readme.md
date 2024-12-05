## Create a bucket

```sh
aws s3 mb s3://encryption-fun-fh2
```

## Create a file

```sh
echo "Hello world" > hello.txt
aws s3 cp hello.txt s3://encryption-fun-fh2
```

## Put Object with encryption of KMS

```sh
aws s3api put-object \
--bucket encryption-fun-fh2 \
--key hello.txt \
--body hello.txt \
--server-side-encryption aws:kms \
--ssekms-key-id $KEY_ID
```

## Put Object with SSE-C

```sh
export BASE64_ENCODED_KEY=$(openssl rand 32 | base64)
echo $BASE64_ENCODED_KEY

export MD5_VALUE=$(echo -n $BASE64_ENCODED_KEY | base64 --decode | md5sum | awk '{print $1}' | base64)
echo $MD5_VALUE

aws s3api put-object \
--bucket encryption-fun-fh2 \
--key hello.txt \
--body hello.txt \
--sse-customer-algorithm AES256 \
--sse-customer-key $BASE64_ENCODED_KEY \
--sse-customer-key-md5 $MD5_VALUE
```

## Put Object with SSE-C v2

```sh
aws s3 cp hello.txt se://encryption-fun-fh2/hello.txt \
--sse-c AES256 \
--sse-c-key fileb://ssec.key

aws s3 cp s3://encryption-fun-fh2/hello.txt hello.txt --sse-c AES256 --sse-c-key fileb://ssec.key
```
