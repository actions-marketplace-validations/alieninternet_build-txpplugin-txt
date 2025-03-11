# `simple.md` - A very simple build and release example

This example workflow will trigger on the publication of a release to 
build a Textpattern plugin into a `.txt` file package and upload the
resulting package to the release.

## Installation

### Assumptions

The following assumptions are made:

* Your Textpattern plugin is stored in the root folder of a repository.
  [An example can be found here](https://www.github.com/alieninternet/ais_feed).
  Note: This can be adjusted with a small modification of the workflow.

* Your file structure matches that needed by the packaging tool.
  [More information is available here](https://github.com/alieninternet/ais_txpplugin_packager/blob/main/README.md).

### Installation steps

1. Copy `simple.md` into your repository's workflow folder, e.g.
   `REPOSITORY/.github/workflows/release.yml`

2. If your Textpattern plugin files (PHP file, textpacks, etc) are not
   located in the root of your repository, modify the workflow to adjust
   the `folder` parameter from `'.'` to the path required to reach your
   plugin source files, for example: `'./src'`.

## Frequency Asked Questions

<details>
 <summary>Q: Why is the plugin name wrong in the package output?</summary>
 A: The plugin name is the same as the repository name, by default.
    You can override this by specifying your own package_filename value
<details>

<details>
 <summary>Q: Why is the version number in the package filename is wrong?</summary>
 A: The version number comes from your plugin's `manifest.json` by default.
    Check there, maybe it has not been updated.
</details>
