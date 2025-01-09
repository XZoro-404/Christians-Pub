Navigate to the root of the project directory example C:\projects\Christians-pub-4 and run the command *npx quartz sync* to push to the Github repo and *npx quartz sync --no-pull* if it is the initialization of the content.

For full help options, you can run `npx quartz sync --help`.

Most of these have sensible defaults but you can override them if you have a custom setup:

- `-d` or `--directory`: the content folder. This is normally just `content`
- `-v` or `--verbose`: print out extra logging information
- `--commit` or `--no-commit`: whether to make a `git` commit for your changes
- `--push` or `--no-push`: whether to push updates to your GitHub fork of Quartz
- `--pull` or `--no-pull`: whether to try and pull in any updates from your GitHub fork (i.e. from other devices) before pushing