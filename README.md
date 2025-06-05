# runpy

Run Python scripts in isolated virtual environments. Each script gets its own venv so dependencies don't clash.

## What it does

- Creates a unique venv for each script (based on script path)
- Auto-installs dependencies from `requirements.txt` 
- Works on Windows, macOS, Linux
- Clean up environments when you're done

## Setup

```bash
chmod +x runpy
# optionally add to PATH
```

## Usage

```bash
./runpy script.py                    # basic usage
./runpy script.py arg1 --flag        # pass arguments  
./runpy -o script.py                 # run once, then cleanup
./runpy -v script.py                 # verbose mode
./runpy -c script.py                 # just cleanup
./runpy -r script.py                 # reset dependencies
```

## Options

- `-o, --run-once` - cleanup after running
- `-c, --clean` - remove environment  
- `-r, --reset` - reinstall dependencies
- `-v, --verbose` - debug output

## How it works

1. Makes a venv at `~/.venv/{script-path-hash}/`
2. Installs from `requirements.txt` if it exists
3. Runs your script
4. Keeps the venv around for next time (unless `-o`)

## Troubleshooting

```bash
./runpy -v script.py     # see what's happening
./runpy -c script.py     # nuke the environment  
./runpy -r script.py     # refresh dependencies
```