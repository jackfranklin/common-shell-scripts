A set of shell scripts that I use quite a lot across different projects, for the times where Grunt / Gulp / etc is just too much.

## Usage

```
npm install --save-dev common-shell-scripts
```

Then you can call a script, for example the `watch` script, like so:

```
./node_modules/common-shell-scripts/watch {arg1} {arg2}
```

The typical usage is to put these into a Makefile, or similar. The [Makefile of Totesy](https://github.com/jackfranklin/totesy/blob/master/Makefile) shows this in action.

## Commands

### `watch`

Watch a directory or file for changes and run something when changes are detected.

```
./watch directory/to/watch command_to_run
```

### `replace_secrets`

Useful for placing secret information (API Keys, etc) in files but not in version control.

Given a JSON file `secrets.json` like so:

```
{ "my_secret_key": "1234ABC" }
```

And `app.js` like this:

```js
var myApiKey = '!my_secret_key!';
```

Running:

```
./replace_secrets secrets.json app.js
```

Will result in `app.js` reading like so:

```js
var myApiKey = '1234ABC';
```


