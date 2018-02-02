* zip a file up from directory level up to package for lambda
  `zip -r ../monster-mall-hi-score-get.zip *`

* set s3 hosting permissions for website
```
{
  "Version":"2012-10-17",
  "Statement":[{
	"Sid":"PublicReadGetObject",
        "Effect":"Allow",
	  "Principal": "*",
      "Action":["s3:GetObject"],
      "Resource":["arn:aws:s3:::example-bucket/*"
      ]
    }
  ]
}
```
