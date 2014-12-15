# Composer nested installer

This installer builds upon [composer/installers](https://github.com/composer/installers) and adds functionality to it.
Originally this was want to be a [pull request for composer/installer](https://github.com/composer/installers/pull/204)

## Usage

Instead of requiring composer installer, you should require `derhasi/composer-nested-installer`.

```
"require": {
  "derhasi/composer-nested-installer": "0.1.*"
}
```

## Additional features

### Preserving subpaths

If some package may be located inside of another package, you need to set its
path to be preserved with the extra option `installer-preserve-subpaths`.

For example a _Drupal_ project may install `drupal/drupal` to the root directory,
whereas _Drupal modules_ (Type: `drupal-module`) will be located at
`modules/{$name}/`. In the case of a `drupal/drupal` package update, all modules
would get overwritten. To preserve that, you then should add to your `composer.json`.

``` json
{
    "extra": {
        "installer-preserve-subpaths": [
            "modules/"
        ]
    }
}
```

Please note that files of the wrapping package might get overwritten by
preserved paths.
