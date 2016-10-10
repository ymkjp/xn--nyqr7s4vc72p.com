# article.xn--nyqr7s4vc72p.com

```bash
aws s3 sync article.xn--nyqr7s4vc72p.com s3://article.xn--nyqr7s4vc72p.com --exclude '.git/*'  --delete --dryrun
```


## Static Website Hosting

* **Index Document:** `index.html`
* **Error Document:** `404.html`

#### Edit Redirection Rules:

```xml
  <RoutingRules>
    <RoutingRule>
    <Condition>
       <KeyPrefixEquals>feed/</KeyPrefixEquals>
    </Condition>
    <Redirect>
      <ReplaceKeyWith>feed/index.xml</ReplaceKeyWith>
    </Redirect>
    </RoutingRule>
  </RoutingRules>
```

## Permissions

#### Edit bucket policy

```json
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Sid": "AddPerm",
			"Effect": "Allow",
			"Principal": "*",
			"Action": "s3:GetObject",
			"Resource": "arn:aws:s3:::article.xn--nyqr7s4vc72p.com/*"
		}
	]
}
```

#### Edit CORS Configuration

```xml
<CORSConfiguration>
    <CORSRule>
        <AllowedOrigin>https://*.xn--nyqr7s4vc72p.com</AllowedOrigin>
        <AllowedMethod>GET</AllowedMethod>
        <MaxAgeSeconds>3000</MaxAgeSeconds>
    </CORSRule>
    <CORSRule>
        <AllowedOrigin>http://*.xn--nyqr7s4vc72p.com</AllowedOrigin>
        <AllowedMethod>GET</AllowedMethod>
        <MaxAgeSeconds>3000</MaxAgeSeconds>
    </CORSRule>
</CORSConfiguration>
```
