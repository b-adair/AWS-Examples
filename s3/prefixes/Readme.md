## Create bucket

```sh
aws s3 mb s3://prefixes-fun-fh2
```


## Create folder

```sh
aws s3api put-object --bucket="prefixes-fun-fh2" --key="hello/"
```


## Create many folders
```sh
aws s3api put-object --bucket="prefixes-fun-fh2" --key="Lorem/ipsum/dolor/sit/amet/consectetur/adipiscing/elit/Nunc/id/facilisis/dolor/Donec"
```