Badcow Fluent Interface
=======================

Turns methods of any non-final class that do not return anything into chainable, fluent interfaces.

## Disclaimer

This is a joke. I made this library after an argument with the senior dev who doesn't like fluent interfaces.
If you can think of a legitimate use for this library, I would like to know.

## Installation

### Using composer

    //composer.json
    {
        "require": {
            "badcow/fluent-interface": "dev-master"
        }
    }

### Other method

Clone the repository and include the autoloader.

    <?php

    require_once 'path/to/fluent-interface/bin/autoload.php';

## Basic Usage

### Non fluent class

    <?php
    //sample_class.php

    namespace Sour\Milk;

    class FooBar
    {
        /**
         * @var string
         */
        private $firstName;

        /**
         * @var string
         */
        private $lastName;

        /**
         * @return string
         */
        public function getFirstName()
        {
            return $this->firstName;
        }

        /**
         * @return string
         */
        public function getLastName()
        {
            return $this->lastName;
        }

        /**
         * @param string $firstName
         */
        public function setFirstName($firstName)
        {
            $this->firstName = $firstName;
        }

        /**
         * @param string $lastName
         */
        public function setLastName($lastName)
        {
            $this->lastName = $lastName;
        }
    }

### Create fluent proxy

    <?php

    use Badcow\FluentInterface\FluentInterface;

    //Set the directory where to store the proxy classes
    $fi = new FluentInterface(__DIR__ . '/Proxies');

    //Create a proxy class. The second parameter forces the recreation of the file.
    $proxy = $fi->create('Sour\Milk\Foobar', true);
    $foobar = new $proxy();

    //Class is now a fluent interface
    $foobar->setFirstName('Sam')->setLastName('Williams');

    echo $foobar->getFirstName() . ' ' . $foobar->getLastName();

## Build Status
[![Build Status](https://travis-ci.org/samuelwilliams/fluent-interface.png?branch=master)](https://travis-ci.org/samuelwilliams/fluent-interface)
