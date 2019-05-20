Using aws s3 cp from the AWS Command-Line Interface (CLI) will require the --recursive parameter to copy multiple files.
aws s3 cp s3://myBucket/dir localdir --recursive

The aws s3 sync command will, by default, copy a whole directory. It will only copy new/modified files.
aws s3 sync s3://mybucket/dir localdir

ref: https://stackoverflow.com/questions/27932345/downloading-folders-from-aws-s3-cp-or-sync



aws s3 cp \
	--dryrun \
	--region REGION_NAME \
	--recursive \
	--content-encoding 'gzip' \
	/path/to/files/ \
	s3://BUCKET_NAME/path/to/dest


aws s3 sync \
	--dryrun \
	--region REGION_NAME \
	--delete \
	/path/to/files/ \
	s3://BUCKET_NAME/path/to/dest