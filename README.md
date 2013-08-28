Dropwizard Spring DI/Security Example
==============================================
 
Example showing how to integrate Dropwizard, Spring DI, Spring Security together.
They are compiled into a single uber-jar using the Gradle Shadow plugin: <https://github.com/johnrengelman/shadow>.

*We used the OneJar plugin before (hence it is in the title of this example), but it caused issues with Dropwizard's  HTML asset loading mechanism, so we replaced it with the Gradle Shadow plugin.*

It also shows how to perform integration testing of a REST application
using the famous BDD tool Cucumber:

http://cukes.info

This application was prepared for a Houston JUG presentation:

https://github.com/jacek99/dropwizard-spring-di-security-onejar-example/raw/master/Dropwizard_Spring.pdf

**Note**

This application uses Lombok:
http://projectlombok.org/

Please make sure you have the appropriate Lombok plugin installed in your IDE.


Gradle tasks
============

gradle idea
-----------

Regenerate IDEA IntelliJ bindings

gradle eclipse
--------------

Regenerate Eclipse bindings

gradle run
----------

Runs the app *main()* method

gradle shadow
-------------

Compiles the entire app together with its dependencies into one single uber-JAR, using the Gradle Shadow plugin

gradle runShadow
----------------

Compiles and runs the Gradle Shadow uber-JAR version of the app

gradle bdd
----------

Runs the uber-JAR on a separate thread and executes the entire BDD test suite against the running application.


Integration testing with BDDs
=============================

Mock frameworks are the false prophets of Java application testing.

Your only surefire way to test your logic is to fire requests at your fully running app and verify its behaviour and responses.
Cucumber-style BDDs are the best and most productive way to accomplish this task IMHO:

http://cukes.info/

To get it fully running and installed do the following:

**Ubuntu / Debian**

    sudo apt-get install ruby ruby-dev libyaml-dev
    sudo gem install bundler
    bundle install

**Fedora / CentOS**

    sudo yum install ruby ruby-devel libyaml-devel
    gem install bundler
    bundle install

**Windows**

Install Ruby 1.9 (NOT 2.0) for Windows: 
http://rubyinstaller.org/

and the Ruby 1.9 DevKit as well:
http://rubyinstaller.org/add-ons/devkit/

Install the dev kit (from the folder where you placed it):

    ruby dk.rb init
    ruby dk.rb install

The rest is similar afterwards:

    gem install bundler
    bundle install

Running BDDs manually
=====================

Run the app from your IDE.

You will need to create a launcher that passes in the **server myapp.yml** program arguments to the main class
MyAppService, as seen in the image below:

https://raw.github.com/jacek99/dropwizard-spring-di-security-onejar-example/master/launcher.png

Go to a terminal and do

	cd src/test/resources/bdd
	cucumber

and you should see a human-readable BDD execute:

https://github.com/jacek99/dropwizard-spring-di-security-onejar-example/blob/master/src/test/resources/bdd/features/country_rest.feature
