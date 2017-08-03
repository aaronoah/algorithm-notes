# algorithm-cracker

Comprehensive algorithms solution to help engineers prepare their interviews and future study :cookie:

## Motivation

Understanding the algorithm mechanism is essential in structuring solutions for specific computation tasks and even more so in abstracting the most challenging questions such as Artificial Intelligence problems or Machine Learning techniques in various fields.

Consider the importance of algorithm analysis in all branches of Computer Science and its novel insights in subjects like quantum mechanics, economic analysis and so on, it is necessary to know the domain knowledge of algorithm in terms of math and logic.

It is especially helpful for students, engineers and scientists to organize algorithm principles online.

## Usage

In order to collaboratively take advantage of this material, usage in the following forms are welcomed:

- Download the [pdf](), [epub]() or [raw html]() versions of the algorithm handbook for self-learning or redistribution under the license constraint.
- Clone or Fork this repo to build your own flavor of algorithm handbook or to submit Pull Request.

### Prerequisites

* [pandoc](http://pandoc.org/) should be installed.
* [wkhtmltopdf](https://wkhtmltopdf.org/index.html) should be downloaded and installed.

In Mac OS X system,
* [MacTex](http://www.tug.org/mactex/), if the distribution is too big for you, consider its smaller subset [basicTex](http://www.tug.org/mactex/morepackages.html).

In Unix/Linux system,
* [TexLive](http://www.tug.org/texlive/acquire-netinstall.html) is required for font generation.

### Build from Source

In your **terminal**, run

```bash
$ alias chrome="PATH/TO/YOUR/CHROME_DESKTOP_BROWSER_APP"
```

and type in the following command (make sure you have _bash_ 4.0+ installed)

```bash
$ . build.sh
```

to supply _options_ --html, --pdf or --epub to generate the corresponding ebook versions for _interactive prompts_ or

```bash
$ . build.sh [--html|--pdf|--epub]
```

to achieve the same effects. Then, the versions you desire are built under the _out_ directory.

## Contributing

Make sure you follow the [contributing guide](.github/CONTRIBUTING.md) in order to proceed with any forms of contribution.

## License

[MIT](https://opensource.org/licenses/MIT), Copyright &copy; 2017, Hanqing Zhao
