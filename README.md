# Premessa
AWS WAF non può essere taggato da console AWS, quindi è necessario un passaggio da CLI.

# Procedura
Facciamo un list della webACL per ottenere l'arn (caso WAF associato a CloudFront):
``` aws wafv2 list-web-acls --scope=CLOUDFRONT --region=us-east-1 --profile XXX ```

Eseguiamo il comando:
``` aws wafv2 tag-resource \
    --resource-arn <ARN> \
    --tags Key=<KEY>,Value=<VALUE> \
    --region=us-east-1 \
    --profile XXX ```

Check:
``` aws wafv2 list-tags-for-resource --resource-arn arn:aws:wafv2:us-east-1:302968333199:global/webacl/fincantieri-si/29672c65-75d3-4131-bbcc-3ba6a9a5c2e1 --region=us-east-1 --profile fincantieri ```
  
