# `alieninternet/build-txpplugin-txt` <br /> Build and release Textpattern plugin packages

Package a Textpattern plugin as a TXT package, and optionally add package to the release that triggered the workflow.

## Theory of Operation

This action downloads and executes the [Textpattern Plugin Packager (ais_txpplugin_packager](https://github.com/alieninternet/ais_txpplugin_packager) 
to produce a plugin package.

Optionally, the resulting files (the TXT plugin package and its SHA-256 checksum file) can be added to the release triggering the workflow automatically.

## Example

Example workflows can be found [here](https://github.com/alieninternet/build-txpplugin-txt/blob/main/examples).
Here is a simple example workflow ([simplified from this example](https://github.com/alieninternet/build-txpplugin-txt/blob/main/examples/simple.md)) 
that builds and releases a plugin package when you publish a release:

```yaml
on:
  release:
    type: [published]

permissions:
  contents: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Check-out repository
        uses: actions/checkout@v4

      - name: Build and release package
        uses: alieninternet/build-txpplugin-txt@v1
        with:
          release_files: 'true'
```

## Usage

*Use* the action from the GitHub actions marketplace by referencing `alieninternet/build-txpplugin-txt@v1`.

### Inputs

<details><summary><h4><code>folder</code> - Folder containing the plugin files</h4></summary>
  Folder containing the plugin files (should include manifest.json).

  If not provided, it is assumed the plugin file is in the current working directory.
  If you haven't changed directory before calling this action, that would be the root of your repository.
</details>

<details><summary><h4><code>package_filename</code> (Optional) - Package filename</h4></summary>
  Optional package filename.

  If not provided, the action will read manifest.json from the specified plugin source folder and construct a filename as 
  <code>&lt;plugin name&gt;_v&lt;version&gt;.txt</code>, with dots in the version replaced by underscores.
</details>

<details><summary><h4><code>release_files</code> (Optional) - Release files?</h4></summary>
  If set to <code>true</code>, automatically add the generated files to the release.
</details>

<details><summary><h4><code>github_token</code> (Optional) - GitHub token</h4></summary>
  This option defaults to the repository scoped GitHub Token.
  
  If you need more permissions for things such as deploying to another repository, you can add a Personal Access Token (PAT) here.
  
  [Learn more about creating and secrets here.](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/creating-and-using-encrypted-secrets)
  </details>

### Outputs

<details><summary><h4><code>output_file</code></h4> - The file name of the package that was built</summary>
  Append <code>.sha256</code> to this for the generated SHA-256 checksum file.
</details>
