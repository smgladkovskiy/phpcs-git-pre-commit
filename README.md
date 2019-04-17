# PHPCS git pre-commit hook

## About

Auto installed git pre-commit hook for running [PHP Code Sniffer](https://github.com/squizlabs/PHP_CodeSniffer) code checking to [PSR-2](https://www.php-fig.org/psr/psr-2/) coding standard compliance. It only checks files that are to be committed.

Inspired by [Enforce code standards with composer, git hooks, and phpcs](http://tech.zumba.com/2014/04/14/control-code-quality/)

## What this fork adds

The user is prompted to automatically apply the fixes to the current commit. Running the code fixer can be disabled altogether by setting the `CODE_FIXER` environment variable to `false`.

These changes are widely inspired from [this tutorial](https://robjmills.co.uk/2018/01/14/automatic-psr2-coding-standard.html), whose proposed script was only slightly updated so the code fixer is run by default and skipped only if the environment variable is set to `false`.

Thanks to [smgladkovskiy](https://github.com/smgladkovskiy/phpcs-git-pre-commit) for the original work.

## Installation

Install `osteel/phpcs-git-pre-commit` with composer require command:

    composer require "osteel/phpcs-git-pre-commit"

Or alternatively, include a dependency for `osteel/phpcs-git-pre-commit` in your composer.json file manually:

    {
        "require-dev": {
            "osteel/phpcs-git-pre-commit": "dev-master"
        }
    }

To enable code sniff, аdd to `post-install-cmd` and `post-update-cmd` in `composer.json` installation script:

    "post-install-cmd": [
        "sh ./vendor/osteel/phpcs-git-pre-commit/src/setup.sh"
    ],
    "post-update-cmd": [
        "sh ./vendor/osteel/phpcs-git-pre-commit/src/setup.sh"
    ]

Then run `composer install` or `composer update`. `pre-commit` hook will be installed or updated if it already exists.

## Usage

Run `git commit` and pre-commit hook will check your committed files like if you run

    php phpcs.phar --standard=PSR2 --encoding=utf-8 -n -p /path/to/file.php

## Contributing

Feel free to make pull requests!
