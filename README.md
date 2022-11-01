## About

A containerized installation of craft, distributed for a testing workshop.

## Dependencies

This project uses Docker to install all of the necessary dependencies within a sandboxed container. To get started, ensure you have the following:

 - [docker](https://www.docker.com/products/docker-desktop/) (or [colima](https://github.com/abiosoft/colima)) : a tool for managing and running containers
 - [ddev](https://ddev.readthedocs.io/en/latest/users/install/ddev-installation/#system-requirements) : a tool that makes docker easier to use

 If you're using homebrew (macOS), the above dependencies can be installed easily:
 - `brew install homebrew/cask/docker`
 - `brew install drud/ddev/ddev`

## Installation

 1. `git clone http://github.com/nickworks/test-demo-craft` to clone the project
 2. `cd test-demo-craft` to navigate into the project directory
 3. `cp .env.example.dev .env` to create an env file 
 4. `ddev start` to run the container
 5. `ddev ssh` to ssh into the container
 6. `composer update` to install PHP packages
 7. `php craft setup/security-key` to generate Craft's Security Key value
 8. `php craft setup/app-id` to generate Craft's App ID value

 ## Stopping the container
 
 - `exit` will close the ssh connection to the container
 - `ddev stop` will stop the container
 - `ddev powerdown` will stop all containers managed by ddev

 ## Testing in Craft

 ### Installing Codeception

 1. `composer require codeception/codeception --dev` will install the package
 2. `codecept bootstrap` will setup the test suites
 3. configure the test suites

 ### Using Codeception

 - `codecept g:cest [suite] [file]` will create a new Cest file
 - `codecept g:test [suite] [file]` will create a new unit test
 - `codecept run` will run all tests
 - `codecept run --no-artifacts` will omit thrown errors
 - `codecept run --html` will generate a coverage report
