Humus PHPUnit Module
====================

Humus PHPUnit Module is a Module for Zend Framework 2 for unit testing.

Installation
------------

 1.  Add `"prolic/humus-phpunit-module": "dev-master"` to your `composer.json`
 2.  Run `php composer.phar install`
 3.  Enable the module in your `config/application.config.php` by adding `HumusPHPUnitModule` to `modules`

Usage
-----

    ./vendor/bin/phpunit

PHPUnitListener
-------------------

There are two ways to configure the PHPUnit Runner.

 1. Implement the HumusPHPUnitModule\ModuleManager\Feature\PHPUnitProviderInterface in your module.
 2. Override the phpunit_runner configuration.

1. Sample Module:

    namespace MyModule;
    
    use HumusPHPUnitModule\ModuleManager\Feature\PHPUnitProviderInterface;
    
    class Module implements PHPUnitProviderInterface
    {
        public function getPHPUnitXmlPaths()
        {
            return array(
                dirname(dirname(__DIR__)) . '/tests/phpunit.xml'
            );
        }
    }

2. Sample Configuration:

    <?php
    return array(
        'humus_phpunit_module' => array(
            'phpunit_runner' => array(
                'Doctrine\Common' => array(
                    'vendor/doctrine/common/phpunit.xml.dist'
                )
            )
        )
    );