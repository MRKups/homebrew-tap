# MRKups Homebrew Tap

Personal [Homebrew](https://brew.sh) tap maintained by [MRKups](https://github.com/MRKups).

The tap is ready for packages. No formulae or casks have been published yet.

## Use this tap

```sh
brew tap mrkups/tap
```

Once packages are available, install them with their fully qualified names
(replace `PACKAGE` with a published package name):

```sh
# Formula: command-line tool or library
brew install mrkups/tap/PACKAGE

# Cask: macOS application
brew install --cask mrkups/tap/PACKAGE
```

The install commands also add the tap automatically.

## Repository layout

- `Formula/`: formula definitions, one `.rb` file per package.
- `Casks/`: cask definitions, one `.rb` file per package.
- `.github/workflows/tests.yml`: Homebrew checks on pushes and pull requests;
  formula builds and bottle artifacts on pull requests.
- `.github/workflows/publish.yml`: manually publish bottles from a tested pull request.
- `.github/workflows/autobump.yml`: scheduled checks for formula updates that open pull requests.
- `.github/dependabot.yml`: weekly GitHub Actions dependency updates.

The workflows were generated with Homebrew's `brew tap-new` command.

## Add the first package

1. Publish a versioned release of the project to package.
2. Create a definition in this tap with
   `brew create --tap mrkups/tap RELEASE_URL` (add `--cask` for a cask).
3. Complete the metadata, versioned download URL, SHA-256 checksum, dependencies,
   and installation steps. Include a functional `test do` block for a formula.
4. Open a pull request and review the Homebrew checks.

For a formula, local checks typically include:

```sh
brew style mrkups/tap/PACKAGE
brew audit --strict --online mrkups/tap/PACKAGE
brew install --build-from-source mrkups/tap/PACKAGE
brew test mrkups/tap/PACKAGE
```

For formulae using Homebrew-built bottles, run the **brew pr-pull** workflow
after the pull request checks pass. Provide the pull request number and the
reviewed head commit SHA; the workflow publishes the bottles and pushes the
resulting commits to `main`.

The local Homebrew tap directory can be a symbolic link to this working copy,
so edits here are immediately available to `brew`.

## Documentation

- [Creating and maintaining a tap](https://docs.brew.sh/How-to-Create-and-Maintain-a-Tap)
- [Formula cookbook](https://docs.brew.sh/Formula-Cookbook)
- [Cask cookbook](https://docs.brew.sh/Cask-Cookbook)
