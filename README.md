# QUT Faculty of Science Canvas Template

This repository contains the markdown files for the QUT Faculty of Science Canvas template. The markdown files are tracked by Chancellor and are used to generate Canvas pages for a unit under the Faculty of Science.

## How to use this repository

This repository is intended to be used with Chancellor, a command-line tool that allows you to manage your Canvas course content using markdown files. 

You can find more information about Chancellor [here](https://www.npmjs.com/package/chancellor-cli).

### Clone the repository

Either use Git, or Chancellor to clone the repository to your local machine:

```bash
git clone https://github.com/Chancellor-LMS/fos-template
```

Or

```bash
chancellor clone https://github.com/Chancellor-LMS/fos-template
```

### Edit the markdown files

Edit the files in the `overview` folder (corresponding to the `Overview` module in Canvas) using your favourite text editor.

Refer to the `examples` folder for examples of how to format your markdown files to be compatible with Chancellor.

### Render the markdown files

For a preview of the markdown files, you can render them using Chancellor:

```bash
chancellor run render
```

### Push the changes to Canvas

Once you are happy with the changes, you can push them to Canvas using Chancellor:

```bash
chancellor run canvas-deploy
```