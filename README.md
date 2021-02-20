# opencart-testing
Functional Unit Testing of the OpenCart System using PHPUnit for the Software Testing Techniques Course.


## Repository Structure

* The `dev` directory contains the OpenCart project in its development version, within this directory the source code that is under development is kept and the functional unit test suite using PHPUnit is also contained.

* The `prod` directory contains the OpenCart project in its production version, within this directory the source code is kept that passes the functional unit tests using PHPUnit.


## Install Dependenias
Before running the project, the dependencies must be installed from the `dev` directory using the composer tool:

`` `sh
$ composer install
`` ''

## Configure Environment Variables for OpenCart

Copy the `.env.sample` file found in the` dev` directory and save it in the same `dev` directory with the file name` .env`.

Modify the environment variables that OpenCart uses as needed:

### OpenCart Database connection values
`` ''
OC_DB_HOSTNAME = localhost
OC_DB_USERNAME = opencart
OC_DB_PASSWORD = opencart
OC_DB_DATABASE = opencart
OC_DB_DRIVER = mysqli
`` ''

### OpenCart Administration user
`` ''
OC_USERNAME = admin
OC_PASSWORD = admin
OC_EMAIL=you@example.com
`` ''

### Server Specification
`` ''
SERVER_PORT = 8000
SERVER_URL = http: // localhost
`` ''


## Run Tests

Functional unit tests are run from the `dev` directory with the following steps:

`` `sh
$ bin / steal opencart: setup (Step 1. Configure the OpenCart environment)
$ bin / robo project: deploy (Step 2. Perform an OpenCart Deploy)
$ bin / phpunit --testsuite catalog-tests (Step 3. Run the catalog tests 'catalog-test' defined in the phpunit.xml suite)
$ bin / steal opencart: run (Step 4. Launch OpenCart server)
`` ''

Step number 4. is optional, to run only the tests it is only necessary to run steps 1. - 3.

### Test Suite

The test suite is configured in the file `dev / phpunit.xml` you can create blocks that make up the suite following the pattern:

xml
<testsuites>
    <testsuite name = "catalog-tests">
        <file> ./tests/HelloWorldTest.php </file>
    </testsuite>
    <testsuite name = "admin-tests">
        <file> ./tests/HelloWorldAdminTest.php </file>
    </testsuite>
</testsuites>
`` ''

All the test files that are created must be saved in the `dev / tests` directory which are part of the test suite. 
