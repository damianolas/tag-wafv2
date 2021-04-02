# Premessa
AWS WAF non può essere taggato da console AWS, quindi è necessario un passaggio da CLI.

# Procedura
Facciamo un list della webACL per ottenere l'arn (caso WAF associato a CloudFront):
``` 
aws wafv2 list-web-acls --scope=CLOUDFRONT (REGIONAL per gli ALB) --region=us-east-1 --profile XXX
```

Eseguiamo il comando:
``` 
aws wafv2 tag-resource \
    --resource-arn <ARN> \
    --tags Key=<KEY>,Value=<VALUE> \
    --region=us-east-1 \
    --profile XXX 
```

Check:
``` 
aws wafv2 list-tags-for-resource \
    --resource-arn <ARN> \
    --region=us-east-1 \
    --profile XXX 
```

Doc: https://docs.aws.amazon.com/cli/latest/reference/wafv2/index.html#cli-aws-wafv2
