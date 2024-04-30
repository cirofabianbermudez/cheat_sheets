## Tools

# pymarkdown

## Installation


```bash
python -m venv .venv
./.venv/Scripts/Activate.ps1
python -m pip install --upgrade pip
pip install pymarkdown
```

## Flags

| Arguments               | Description                                    |
| ----------------------- | ---------------------------------------------- |
| `version`               | Version of the application                     |
| `scan`                  | Scan the Markdown file in any specified path   |
| `fix`                   | Fix any Markdown files in any specified paths  |
| `extensions list`       | Request information on current extensions      |
| `extension info <name>` | Request information about `<name>` extension   |
| `plugins list`          | Request information on current plugin rules    |
| `plugins info <name>`   | Request information about `<name>` plugin rule |

| Flags                   | Description                                        |
| ----------------------- | -------------------------------------------------- |
| `--help`, `-h`          | Shows help message                                 |
| `--config`, `-c`        | Path to the configuration path to use              |
| `--set`, `-s`           | Manually set an individual configuration property  |
| `--enable-rules`, `-e`  | Comma separated list of rules (plugins) to enable  |
| `--disable-rules`, `-d` | Comma separated list of rules (plugins) to disable |

## Usage

### Scan

Scan all the files in the directory

```bash
pymarkdown scan directory/
```

Scan a single file

```bash
pymarkdown scan filename.md
```

If you want to know extra information about the rule use:

```bash
pymarkdown plugins info <name>
```

## Fix

Fix the warnings given by scan in the directory

```bash
pymarkdown fix directory/
```

Fix the warnings given by scan of a single file

```bash
pymarkdown fix filename.md
```

You can use the following flags with the `scan` and `fix` command:

| Flags                | Description                                                             |
| -------------------- | ----------------------------------------------------------------------- |
| `--list-files`, `-l` | List any eligible Markdown files found on the specified paths and exit. |
| `-recurse`, `-r`     | Recursively traverse any found directories for matching files           |

## Configuration

To manage all all the plugins and extension it is better to use a `.pymarkdown.yml` file with your custom settings. Here is an example:

```yml
extensions:
  front-matter:
    enabled: true

plugins:
  md002:
    enabled: false
  md013:
    enabled: true
    line_length: 110
```

If you want to specify a custom fie you con do it with:

```bash
pymarkdown --config .pymarkdown_custom.yml scan file.md
```

If you want to keep using the terminal for the complete command to enable the front-matter extension use:

```bash
pymarkdown --set extensions.front-matter.enabled=$!True
```

## References

- [Pymarkdown GitHub](https://github.com/jackdewinter/pymarkdown)
- [The Markdown Guide](https://www.markdownguide.org/)
- [GitHub Flavored Markdown Spec](https://github.github.com/gfm/)