# `simple.md` - A very simple build and release example

This example workflow will trigger on the publication of a release to 
build a Textpattern plugin into a `.txt` file package and upload the
resulting package to the release.

<details>
 <summary><h2>Theory of Operation</h2></summary>

When you publish a new release, this workflow will trigger and execute 
the following steps:

1. Check out your repository.

2. Build your plugin with the name <name>_v<version>.txt along with a
   SHA-256 hash. The name of the plugin will be the same as your
   repository name, and the version will come from the version specified
   in your plugin's `manifest.json` file.
   
3. Add the resulting files to your release.
</details>

<details>
 <summary><h2>Installation</h2></summary>

### Assumptions

The following assumptions are made:

* Your Textpattern plugin is stored in the root folder of a repository.
  [An example can be found here](https://www.github.com/alieninternet/ais_feed).
  Note: This can be adjusted with a small modification of the workflow.

* Your file structure matches that needed by the packaging tool.
  [More information is available here](https://github.com/alieninternet/ais_txpplugin_packager/blob/main/README.md).

* Your Textpattern plugin name is the same as your repository name,
  i.e. <prefix>_<pluginname>

### Installation steps

1. Copy [`simple.md`](https://github.com/alieninternet/build-txpplugin-txt/blob/main/examples/simple.yml) into your repository's workflow folder, e.g.
   `REPOSITORY/.github/workflows/release.yml`

2. If your Textpattern plugin files (PHP file, textpacks, etc) are not
   located in the root of your repository, modify the workflow to adjust
   the `folder` parameter from `'.'` to the path required to reach your
   plugin source files, for example: `'./src'`.
</details>

<details>
 <summary><h2>Frequency Asked Questions</h2></summary>

 <details>
  <summary><h3>Why is the plugin name wrong in the package output?</h3></summary>
  The plugin name is the same as the repository name, by default.
  You can override this by specifying your own package_filename value
 </details>

 <details>
  <summary><h3>Why is the version number in the package filename is wrong?</h3></summary>
  The version number comes from your plugin's `manifest.json` by default.
  Check there, maybe it has not been updated.
 </details>
</details>
