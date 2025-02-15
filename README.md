# puppeteer-cli

A command-line wrapper for generating PDF prints and PNG screenshots with [Puppeteer](https://developers.google.com/web/tools/puppeteer). Aims to be a easy replacement for the deprecated wkhtmltopdf.

## Install

```bash
cd /usr/lib/node_modules/
git clone ...
cd puppeteer-cli
npm i
cd /usr/bin/
ln -s ../lib/node_modules/puppeteer-cli/index.js puppeteer
```

## Usage

```bash
puppeteer print <url> [output]

Print an HTML file or URL to PDF

Options:
  --version                Show version number                         [boolean]
  --help                   Show help                                   [boolean]
  --sandbox                                           [boolean] [default: false]
  --timeout                                            [number] [default: 30000]
  --wait-until                                        [string] [default: "load"]
  --cookie                 Set a cookie in the form "key:value". May be repeated
                           for multiple cookies.                        [string]
  --background                                         [boolean] [default: true]
  --margin-top                                               [default: "6.25mm"]
  --margin-right                                             [default: "6.25mm"]
  --margin-bottom                                           [default: "14.11mm"]
  --margin-left                                              [default: "6.25mm"]
  --format                                                       [default: "A4"]
  --landscape                                         [boolean] [default: false]
  --display-header-footer                             [boolean] [default: false]
  --header-template                                       [string] [default: ""]
  --footer-template                                       [string] [default: ""]
```

```bash
puppeteer screenshot <url> [output]

Take screenshot of an HTML file or URL to PNG

Options:
  --version          Show version number                               [boolean]
  --help             Show help                                         [boolean]
  --sandbox                                            [boolean] [default: true]
  --timeout                                            [number] [default: 30000]
  --wait-until                                        [string] [default: "load"]
  --cookie           Set a cookie in the form "key:value". May be repeated for
                     multiple cookies.                                  [string]
  --full-page                                          [boolean] [default: true]
  --omit-background                                   [boolean] [default: false]
  --viewport         Set viewport to a given size, e.g. 800x600         [string]
```

## Example

``` shell
echo "<h1>Hello world!</h1>" > mypage.html
puppeteer print mypage.html myprint.pdf # local file
puppeteer print https://github.com/JarvusInnovations/puppeteer-cli puppeteer-cli.pdf # url
puppeteer screenshot mypage.html myscreenshot.png # local file
puppeteer screenshot https://jarv.us myscreenshot.png # url
puppeteer screenshot https://jarv.us myscreenshot.png --viewport 300x200
```

## Roadmap

- [X] Add `print` command
- [X] Add support for `http://` inputs in addition to local file paths
- [X] Add `screenshot` command
- [ ] Add compatibility with `wkhtmltopdf` parameters to provide a drop-in replacement?
- [ ] Detect `.json` or `.js` files as input to `screenshot` command instead of a single HTML file or URL, specifying a set of screenshots to capture in series