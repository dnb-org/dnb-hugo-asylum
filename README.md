# DNB-Hugo/ASYLUM

Test cases, issue recreation, bug hunting

Work in progress... Check issue tracker to see what's missing or request others.

## Usage

To be written ...

## Publishing

- Setup signed tags with `npm config set sign-git-tag true`
- Create patch release with `npm run release`
- Create minor release with `npm run release:minor`
- Create major release with `npm run release:major`

## Local Development Environment

### Pre-commit

If you want then install and setup `pre-commit` to check commits for quality and security. This requires Python to be installed. Then run the following commands to set up `pre-commit` locally:

```shell
pip install pre-commit
pre-commit install
```

Other `pre-commit` commands are:

```shell
pre-commit run --all-files # check rules on all files
pre-commit autoupdate # update repositories
pre-commit gc # garbage collection
```

## NPM scripts

### Installation and Setup

```shell
npm install
```

### Development server

Add a file named `.env` to the root of your repository containing your local setup:

```ini
IP=192.168.1.201
PORT=1313
ALGOLIA_APP_ID=
ALGOLIA_API_KEY=
ALGOLIA_INDEX_NAME=
```

Do NOT commit this file to the repository.

To run the development server run

```shell
npm run server
```

## Repository Setup

- To enable step debug logging for the GitHub Workflows, you must set the following secret in the repository that contains the workflow: ACTIONS_STEP_DEBUG to true.

## Development

### Structure (Branches)

($ in front of a slug mean that the slug is not fixed and will vary over multiple branches)

- `main` - main branch with runnable testing suite and Hugo versions
- `testing/testing` - testing, testing, 1 2 3, used for development before being merged ino `main`
- `testing/$test-case-name` - branches with a single test case that depends on a fixed binary version
- `discourse/$thread-name` - branches with samples that are created for threads in https://discourse.gohugo.io
- `howto/$howto-name` - branches that explain one single thing
- `content` - branch for collecting content samples to cherry-pick between branches
- `templates/$template-name` - branches with repos set up for certain site types

### Binaries

**Configuration**: Check out the file `dotfiles/.releases.dist`. In it you find version numbers of hugo that will be
downloaded. To download different versions, then copy the file to `dotfiles/.releases` and edit to your needs.

**Download**: Run `./bin/gethugo.sh`, answer which versions (standard, extended or both) you want to download and lean
back. It will take a while if you have many versions to download. The downloaded binaries will be saved inside the
`bin/hugo` directory.

**ToDo**:

- Create a script that links the preferred hugo binary to hugo
- Create a script that runs through a list of versions and executes commands for each of these version.

## Frequently Asked Questions

### Why not use Git LFS (Large File Storage) for the binaries

Because the free tier has only available space of 1GB and I am using too many different binaries.

## Other elements in DNB Hugo

[DNB Hugo](https://github.com/dnb-org) are the elements that enhance and simplify your daily work with [Hugo, the world's fastest framework for building sites](https://gohugo.io/). Included are:

| Element | Description |
| :--- | :--- |
| [blocks](https://github.com/dnb-org/blocks) | Blocks are reusable page elements like headers, footers, content display etc.|
| [components](https://github.com/dnb-org/components) | Components are preconfigured features like automatic search index creation, sitemap and robots.txt creation, etc. |
| [configurations](https://github.com/dnb-org/configurations) | A collection of configuration packages used in dnb-org |
| [debug](https://github.com/dnb-org/dnb-hugo-debug) | Debugging for your Hugo layout files. |
| [hooks](https://github.com/dnb-org/dnb-hugo-hooks) | Template hooks for Hugo themes |
| [libraries](https://github.com/dnb-org/libraries) | Libraries are a collection of often used external packages, conveniently configured as modules for Hugo. |
| [shortcodes](https://github.com/dnb-org/shortcodes) | Shortcodes are content particles that helpfully solve repeated tasks, like presentation, galleries and so on. |
| [testcontent](https://github.com/dnb-org/testcontent) | Testcontent is a collection of testing content. |
