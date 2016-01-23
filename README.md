# esmake

esmake is a GNU Make Makefile that is shared by a multitude of coldrye-es projects.

It also contains simple project templates for setting up new coldrye-es projects.


## Motivation

or: Why GNU Make and not Grunt or Gulp or ...?

The current situation with the available task runners is so that Gulp is not my
cup of tea and that Grunt lacks active development. Other task runners simply
do not do the trick or are way too specialized for my purposes.

Also, see (2) under resources below for my overall motivation. Opposed to the
view expressed by the author, though, I even refrain from using **npm** for
my build process as this also turned out to be an actual pain in the arse.

Besides, have a look at the available Makefiles and decide for yourself whether
using Grunt or Gulp would have made things easier or even more complex.


## Development Dependencies

Development dependencies must be installed globally as we need the cli commands
provided by those packages.

Besides the dependencies listed in package.json#globalDevDependencies, you need
have the following tools installed.

 - GNU Make


## Usage

### Initialize a new Software Project

Just run

```
> mkdir myproject
> cd myproject
> npm install coldrye-es/esmake
> cp -r node_modules/esmake/templates/software/* .
> cp -r node_modules/esmake/templates/software/.??* .
```

and edit the available files like **package.json**, **.babelrc** and so on as
neccessary.


## Build Process

In order to build a project based on this from source, you need a working Bash.
 
After having cloned that project, you first need to run

```
npm install coldrye-es/esmake
```

after which you can install the required dependencies

```
make deps deps-global
```

Please note that the **deps-global** target requires you to have **sudo** access.


## Makefile.software.in

Makefile.software.in is used with software projects that have been derived from
or are based upon **templates/software**.


### cover

cover makes sure that the test coverage is up to par with that configured in the
.istanbul.json configuration file.

Note that a dummy test file will be generated that will import all of the
available sources to make sure that the coverage information is correct.

If this leads to a build error, feel free to override the internal **$(covercurried)** target.


### deps

Installs both the local runtime and local dev dependencies.


### deps-global

Installs the global dependencies. Requires **sudo**.


### dist

Builds the distribution folder from the available sources. Implies lint and cover.


### doc

Generates API documentation using **esdoc**. You can configure this further by
setting the API documentation targets in the project's Makefile, e.g.

```
doc = dev pub
```

will generate both the developer and the public API documentation. Leaving out
any one of **dev** or **pub** will generate less documentation.


### lint

Lints all available sources and tests using **eslint**.


### publish

Publishes the master branch to the npm repository. There are a few sanity checks
in place that prevent you from publishing an empty package, or, publish from a
different branch than master, or, publish a master that has uncommitted changes.


### test

Runs all available tests using **mocha**.


### watch

Runs a watch process that will update both the documentation and the coverage
information whenever the sources or tests or relevant configuration files have
been changed.


### update-commons

Updates CONTRIBUTING.md, .esdoc*.json and .travis.yml to the versions from the
template.


## Resources

 - (1) [Github Site](https://github.com/coldrye-es/esmake)
 - (2) [Keith Cirkel on "Why we should stop using Grunt & Gulp"](http://blog.keithcirkel.co.uk/why-we-should-stop-using-grunt)

