# Swagger

## Notes

- Language specification [here](https://swagger.io/docs/specification/about/) (latest version)
- JSON or YAML

## Validate

```
docker run -v $(pwd)/swagger:/local swaggerapi/swagger-codegen-cli validate -i /local/api.yaml
```

## HTML rendering

```
docker run -v $(pwd)/swagger:/local swaggerapi/swagger-codegen-cli generate -i /local/api.yaml
```

OR

https://github.com/bootprint/bootprint-openapi


https://bootprint.knappi.org/bootprint/3f1a77b37d612fe0ab9f161f777ffb75b74cffea/bundle.html#operation--accounts--account_id--get

## Mock Server



## Test implementation

https://dredd.readthedocs.io/en/latest/index.html

```
npm install -g dredd
dredd ./api.md http://localhost:3000
```
