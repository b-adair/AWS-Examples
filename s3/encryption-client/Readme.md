## Create a bucket

```sh
aws s3 mb s3://encrypt-client-fun-fh2
```

## Create a file

```sh
echo "Hello World" > hello.txt
```

## Run the SDK ruby script

```sh
bundle exec ruby encrypt.rb
```

## Cleanup

```sh
aws s3 rm s3://encrypt-client-fun-fh2/hello.txt
aws s3 rb s3://encrypt-client-fun-fh2
```
