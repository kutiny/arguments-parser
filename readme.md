# arguments-parser

A simple and configurable node arguments parser

## Configuration

1. Create a folder named _config_.
2. Create a file named _arguments-parser.json_ inside _config_ folder.
3. Create an array of available arguments strings inside _arguments-parser.json_ file.

## Example: _arguments-parser.json_

```js
["--styles", "--routing", ["--port", "-p"]];
```

Note that the third config element is an array of strings, it can be used to assign two or more flags to same configuration.
This configuration for *arguments-parser* will produce this json when we call node with:

```js
node index.js --skipgit --port 4200 -p 3200 --styles=scss
```

### Result object
```json
    {
        "--skipgit": true,
        "--styles": "scss",
        "--port": 4200
    }
```

```js
node index.js --skipgit --p 3200 --port 4200 --styles=scss
```

### Result object
```json
    {
        "--skipgit": true,
        "--styles": "scss",
        "--port": 4200
    }
```

>   As you can see, the first element of the array (for multiple flags to same configuration) is the key of the result object, and has more height than other flags (for same configuration, in this case "-p" vs "--port" is sended in de node command, the result will be builded with "--port" value)

## Other considerations

- In the previous examples the --style flag value has an equal before the value itself, you can define your values with '=' or with a whitespace.
- If no value has passed into a parameter, by default equals true