# WordPress Docker configuration

## How to use
Add your user  to http group ``sudo usermod -aG http $USER``

You need on first time run ``start.sh`` for next times just ``docker compose up -d`` or ``docker compose up``
### How to install coding standards
In root folder run ``composer install`` for istalling coding standards than use next instructions for different text editors:

* [PhpStorm](https://www.jetbrains.com/help/phpstorm/using-php-code-sniffer.html)
* [VS Code](https://sridharkatakam.com/set-wordpress-coding-standards-visual-studio-code/)

# <span style="color:#ff0000">Notice!!!!</span>
During installation of codding standards you may see this error ``ERROR: Referenced sniff "PHPCompatibility.FunctionUse.RemovedFunctions" does not exist
``

<b>Fix:</b> In the ``vendor/squizlabs/php_codesniffer/src/Util/Standards.php`` file add 
```php
$vendorDir = dirname(dirname(dirname(dirname(__DIR__))));
$phpCompatibilityDir = $vendorDir . '/phpcompatibility/php-compatibility/PHPCompatibility';
if (is_dir($phpCompatibilityDir)) {
    $resolvedInstalledPaths[] = $phpCompatibilityDir;
}
```
after this variable ```$resolvedInstalledPaths = [];```