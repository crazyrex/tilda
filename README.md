# clp
A tiny and fast command line arguments parser and help generator.

## Installation
```sh
$ npm i clp
```

## Documentation
### `CLP.Option(aliases, description, name, def)`
Creates a new `CLPOption` instance.

Usages:

```js
CLP.Option(["age", "a"], "The age value.", "age", 20);
CLP.Option("age", "The age value.", "age", 20);
CLP.Option({
    aliases: ["age", "a"]
  , description: "The age value."
  , name: "age"
  , def: 20
  , handler: function (opt) {
       // Do something with opt
    }
});
```

#### Params
- **Array|Object** `aliases`: An array of strings representing the aliases  (e.g. `["name", "n"]`), a string representing a single alias (e.g. `"name"`)
 or an object containing the following fields:

 - `aliases` (Array): An array of strings representing the
    aliases (e.g. `["name", "n"]`)
 - `def` (Anything): The default value.
 - `description` (String): The option description.
 - `name` (String): The option name. If provided, the parser will expect a value otherwise
   will return or display an error.
 - `handler` (Function): The option handler which will be called when the
   option is found in the arguments. The first parameter is the option
   object and the scope is the `CLP` instance.

- **String** `description`: The option description.
- **String** `name`: The option name.
- **Anything** `def`: The default value.

#### Return
- **CLPOption** An object containing the following fields:  - `aliases` (Array): An array of strings containing the computed aliases,
    the single letter being the first ones (e.g. `["-n", "--name"]`).
 - `value` (null|String|DefaultValue): The option value which was found
    after processing the arguments.
 - `def` (Anything): The provided default value.
 - `description` (String): The option description.
 - `name` (String): The option name.
 - `is_provided` (Boolean): A flag if the option was or not been provided.

### `CLP(args, options, clpOptions)`
Creates a new `CLP` (command line parser) instance.

Usage

```js
var parser = new CLP(); // will take the arguments from `process.argv`
var parser = new CLP(args); // default options, empty clpOptions
var parser = new CLP(options, clpOptions); // default arguments
var parser = new CLP(args, clpOptions); // default options
var parser = new CLP(args, options, clpOptions); // pass everything
```

#### Params
- **Array** `args`: An array of strings with the arguments.
- **Object** `options`: An object containing the following fields:
 - `allow_exit` (Boolean): A flag to allow exit or not (e.g. when `-h`
   is passed). This is useful when *CLP* is used in executable scripts,
   however, when you only want to parse an array you should turn this
   off (default: `true`).
 - `help_opt` (Boolean): A flag to add the help option (default: `true`).
 - `version_opt` (Boolean): A flag to add the version option (default: `true`).
 - `name` (String): The application name (default: `"No Name"`).
 - `exe` (String): The executable name (default: `"no-name"`).
 - `version` (String): The application version (default: `"No Version"`).
 - `process` (Boolean): A flag to process the CLP options imediatelly (default: `false`).

- **Array** `clpOptions`:

#### Return
- **CLP** The `CLP` instance.

### `addHelpOption(args, desc)`
Adds the help option.

#### Params
- **Array** `args`: Optional alias options for the help option (default: `["h", "help"]`).
- **String** `desc`: The help description (default: `"Displays this help."`).

#### Return
- **CLP** The `CLP` instance.

### `addVersionOption(args, desc)`
Adds the help option.

#### Params
- **Array** `args`: Optional alias options for the version option (default: `["h", "help"]`).
- **String** `desc`: The version description (default: `"Displays version information."`).

#### Return
- **CLP** The `CLP` instance.

### `addOption(opt)`
Adds a new option to parse.

#### Params
- **CLPOption** `opt`: The `CLPOption` value to add.

#### Return
- **CLP** The `CLP` instance.

### `process()`
Processes the arguments and adds the values in the options.

#### Return
- **CLP** The `CLP` instance.

### `error(err_code, fields)`
Creates an error by getting the error code and the error fields.

#### Params
- **String** `err_code`: The error code.
- **Object** `fields`: An object with the error fields.

#### Return
- **Error** The error which was built.

### `displayHelp()`
Generates the help content and returns it.

#### Return
- **String** The help information.

### `displayVersion()`
Returns the version information.

#### Return
- **String** The version information.


## How to contribute

1. File an issue in the repository, using the bug tracker, describing the
   contribution you'd like to make. This will help us to get you started on the
   right foot.
2. Fork the project in your account and create a new branch:
   `your-great-feature`.
3. Commit your changes in that branch.
4. Open a pull request, and reference the initial issue in the pull request
   message.

## License
See the [LICENSE](./LICENSE) file.