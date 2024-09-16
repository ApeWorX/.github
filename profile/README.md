# Welcome, Apes!

We are [ApeWorX LTD](https://apeworx.io), a collective of infrastructure engineers, smart contract devs, and Web3-curious folks,
building the next generation of Python tooling and infrastructure to support your next great idea.
Our suite of open source projects and developer tools, educational conten, and hosted services aims to guide you along your
journey from idea to production, supporting you beyond the launch to ensure you build the highest quality projects.

Come chat with us online on Discord or X (twitter) to stay up to date on new releases, plugins, and tutorials!

[![Discord chat][discord-badge]][discord-url]
[![Twitter][twitter-badge]][twitter-url]

## Our Projects

### Ape

[Ape Framework](https://apeworx.io/framework) is an easy-to-use Web3 development tool.
Users can compile, test, and interact with smart contracts all in one command line session.
With our [modular plugin system](https://docs.apeworx.io/ape/stable/userguides/quickstart.html#plugin-system),
Ape supports multiple smart contract languages, chains, developer tools/services, and more!

### Silverback

[Silverback](https://apeworx.io/silverback) lets you create and deploy your own Python bots that respond to on-chain events.
The Silverback library leverages Ape Framework as well as it’s ecosystem of plugins and packages to enable you to develop
simple-yet-sophisticated automated applications that can listen and respond to live chain data in real time.
To get started developing with Silverback, check out our [Quickstart Userguide](https://docs.apeworx.io/silverback/stable/userguides/quickstart)
or visit [https://silverback.apeworx.io](https://silverback.apeworx.io) to sign up for the Silverback cloud-hosted application platform.

## Resources

Visit our [technical documentation hub](https://docs.apeworx.io) to get a deeper understanding of Ape, Silverback and our other OSS packages.

<!-- Read our [academic platform](https://academy.apeworx.io/) will help you master Ape Framework with tutorials and challenges. -->

## Contributing

To get started with working on our codebases, use the following steps to prepare your local environment:

```bash
# clone the GitHub repo and navigate into the folder
git clone https://github.com/ApeWorX/[project name].git
cd [project name]

# create and load a virtual environment
python3 -m venv venv
source venv/bin/activate

# install the developer dependencies (-e is interactive mode)
pip install -e .'[dev]'
```

```{note}
You might run into issues where you have a local install and are trying to work with a plugin pinned to a specific version.
```

[The easiest solution](https://github.com/ApeWorX/ape/issues/90) to this is to fetch the tags via `git fetch upstream --tags` and reinstall via `pip install .`.
You will then have the correct version.

### Pre-Commit Hooks

We use [`pre-commit`](https://pre-commit.com/) hooks to simplify linting and ensure consistent formatting among contributors.
Use of `pre-commit` is not a requirement, but is highly recommended.

Install `pre-commit` locally from the root folder:

```bash
pip install pre-commit
pre-commit install
```

Committing will now automatically run the local hooks and ensure that your commit passes all lint checks.

### GitHub Access Token

If you are a member of ApeWorX and would like to install private plugins,
[create a GitHub access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

Once you have your token, export it to your terminal session:

```bash
export GITHUB_ACCESS_TOKEN=<your-token>
```

It is also useful to have this token for local development as some features of Ape communicate with GitHub, and may rate limit you otherwise without it.

### Displaying the Docs
First, make sure you have the docs-related tooling installed:

```bash
pip install -e .'[doc]'
```

Then, run the following from the root project directory:

```bash
python build_docs.py
```

For the best viewing experience, use a local server:

```bash
python -m http.server --directory "docs/_build/" --bind 127.0.0.1 1337
```

Then, open your browser to `127.0.0.1:1337` and click the `ape` directory link.

```{note}
Serving from `"docs/_build/"` rather than `"docs/_build/ape"` is necessary to make routing work.
```

### Submitting Pull Requests

Pull requests are welcomed! Please adhere to the following:

- Ensure your pull request passes our linting checks
- Include test cases for any new functionality
- Include any relevant documentation updates

It's a good idea to make pull requests early on.
A pull request represents the start of a discussion, and doesn't necessarily need to be the final, finished submission.

If you are opening a work-in-progress pull request to verify that it passes CI tests, please consider
[marking it as a draft](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests#draft-pull-requests).

Join the ApeWorX [Discord][discord-url] if you have any questions.


[discord-badge]: https://img.shields.io/discord/922917176040640612.svg?logo=discord&style=flat-square
[discord-url]: https://discord.gg/apeworx
[twitter-badge]: https://img.shields.io/twitter/follow/ApeFramework
[twitter-url]: https://x.com/ApeFramework
