# [API Blueprint](https://apiblueprint.org)

## Notes

- Language specification [here](https://github.com/apiaryio/api-blueprint/blob/master/API%20Blueprint%20Specification.md)
- Based on [Github Flavored Markdown](https://help.github.com/articles/github-flavored-markdown)

## Validate

https://github.com/apiaryio/drafter

## HTML rendering

https://github.com/danielgtaylor/aglio

```
# Build HTML documentation using the default theme
docker run -v $(pwd):/tmp -t dgellow/aglio -i /tmp/api.md -o /tmp/index.html

# Three columns view
docker run -v $(pwd):/tmp -t dgellow/aglio -i /tmp/api.md --theme-template triple -o /tmp/index.html
```

## Mock Server

https://github.com/Aconex/drakov

```
docker run --rm -it -p 3000:3000 -v $(pwd):/workdir dgellow/drakov -f /workdir/api.md --public
```

## Test implementation

https://dredd.readthedocs.io/en/latest/index.html

```
npm install -g dredd
dredd ./api.md http://localhost:3000
```
