![peon](https://user-images.githubusercontent.com/29997/28050411-5b3d7910-65b2-11e7-8539-5f80e6e980ad.png)

# peon

`peon` is a bash script runner. It is inspired by the likes of [rake](https://ruby.github.io/rake/) and [thor](http://whatisthor.com/), but is written in pure bash. The point of `peon` is to be fast and simple. `peon`'s feature set is intentionally very limited.

## Install

### macOS

You can install via [Homebrew](https://brew.sh/):

```bash
brew tap neezer/formulae
brew install peon
```

### Linux

Just download the [latest release](https://github.com/neezer/peon/releases) and extract to a folder in your run path.

You will need to have [`gawk`](https://www.gnu.org/software/gawk/) installed.

## Use

`peon` works out of the directory you call it from. In the current working directory, `peon` expects there to be a `.peon` configuration file. 

***At minimum***, you must tell `peon` where to find your bash scripts, via the `TASKS_IN` variable:

```bash
TASKS_IN=path/to/your/scripts
```

After that, you should be able to run

```shell
$ peon --comands
```

... and see a list of available commands.

## Make your scripts visible to `peon`

In order for `peon` to find, parse, and call scripts, you'll need to add some metatdata to your script files. This can be located anywhere inside the script itself, though it's nice to stick 'em a the top close to the shebang.

```bash
# peon:label => cowsay
# peon:desc  => Prints a cow to stdout with a speech bubble containing your text
```

The value for `peon:label` will be how you invoke this script with `peon`, eg.

```shell
$ peon cowsay
```

The value for `peon:desc` will show up next to your command in the output from the commands flag, eg.

```shell
$ peon --commands

Available commands are:

  cowsay        Prints a cow to stdout with a speech bubble containing your text

```

NOTE: Any script that does not contain this metadata will be invisible to `peon`!

## Configuration

You can further configure `peon` by adding some additional variables to your local `.peon` file:

```bash
# will automatically source a local .env file,
# if one exists, before each command
AUTOLOAD_ENV=true
```

## Contributing

Check out `peon`'s [issues](https://github.com/neezer/peon/issues)!
