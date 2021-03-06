# Sherlock.js

<p align="center">
  <br>
  <img alt="Screenshot" src="https://github.com/GitSquared/sherlock-js/raw/master/screenshot.png" />
  <br><br>
</p>

This is a "remake" of the original [sherlock](https://github.com/sdushantha/sherlock) written in Python by [sdushantha](https://github.com/sdushantha) that I made mostly because I was bored and found that it had some flaws.

It is written in Node.js simply because that's the language I'm the most confortable with, but that's probably not the best choice and I'll see if I can make a Rust version or something.

Notable differences compared to `sherlock` (at time of writing):

 - [0 dependencies pre-built binaries for Windows/macOS/Linux](https://github.com/GitSquared/sherlock-js/releases)
 - Tests all services concurrently (asynchronous/"multithreaded")
 - Checks whether accounts exists by looking at both the HTTP response status code and stripping down the HTML code to search if the desired username is written on the page
 - Follows HTTP(S) redirections
 - Command line switches allow piping output, "batch" mode for use via an external script

### Available command line switches
 - `--help`: Display CLI switches & a link to the GitHub repo
 - `--version` or `-v`: Print version
 - `--name user` or `-n user`: Specify a username to search for (remove interactive prompt)
 - `--batch` or `-b`: Output results in raw minified JSON
 - `--output res.json` or `-o res.json`: Print minified JSON results in a file

### Usage example
Using sherlock.js, it's easy to batch-process a number of usernames by simply using CLI options and `xargs` on Linux.

Assuming we have a `names.txt` file containing one username per line, running:

```
/bin/cat names.txt | xargs -l ./sherlockjs --batch -n
```

...will scan each name in the file in order, and print a machine-readable JSON output to `stdout` on each test.
