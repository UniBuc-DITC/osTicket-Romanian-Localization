# osTicket Romanian localization

This repo contains our updated and fixed versions of osTicket's Romanian translation files.

## Usage

To use these translations, simply clone the repository to your osTicket install's `include/i18n` folder, with the `ro` name.

For example:

```sh
cd include/i18n
git clone git@github.com:UniBuc-DITC/osTicket-Romanian-Localization.git ro
```

Romanian should then pop up as an available language in the admin settings page.

## Updating with new translations from upstream

The latest official osTicket language packs can be downloaded [from their website](https://osticket.com/download/).

To extract the downloaded `.phar` files, you will need to install [the PharUtil package](https://github.com/GabrielMajeri/phar-util).

Then switch to the `upstream` branch and run:

```sh
phar-extract ro.phar .
```

Commit the changes and switch to the `main` branch. Rebase and force-push the commits to the repo.

Existing contributors will have to use `git pull --rebase` to update their local versions.

## Building production language pack

Before deploying to production, you might want to repackage the translations as a `.phar` file to improve performance.

You can do so using the `phar-build` command from the package mentioned above:

```sh
phar-build --ns --src . --phar ro.phar
```

Then, in production, instead of cloning this repository, put the `ro.phar` file into `include/i18n`.

## License

Since translations are considered modifications of the original osTicket source code, they are licensed under the same terms as the original repository (GNU General Public License, version 2).
