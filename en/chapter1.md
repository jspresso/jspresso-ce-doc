A Jspresso application from A to Z
==================================

This chapter will help you to understand the basics of the Jspresso
application framework and how to work with it.

Setting-up the development environment
======================================

One of the interesting feature of Jspresso is its native integration
with standard build tools. All the complex build process is completely
handled in [Maven](http://maven.apache.org/). Jspresso also offers a
Maven archetype to quickly setup your project and import it directly in
[Eclipse](http://www.eclipse.org/).

Installing the tools
--------------------

Download, install and configure the following tools :

-   The [Java Development
    Kit](http://java.sun.com/javase/downloads/index.jsp) for your
    platform (JDK 6+).

-   The [Apache Maven](http://maven.apache.org/download.html) project
    management tool (3.0+).

-   The [Eclipse IDE for Java EE
    Developers](http://www.eclipse.org/downloads/) (3.6+).

-   the [Apache Tomcat servlet
    container](http://tomcat.apache.org/download-60.cgi) (6.0+).

You must also increase the java heap space allocated to Maven :

-   on windows : `set MAVEN_OPTS=-Xmx512m` (or set it as a user env
    variable)

-   on linux : `export MAVEN_OPTS=-Xmx512m` (or set it as a user env
    variable)

Generating the skeleton project
-------------------------------

This is a one-step operation using the Jspresso application Maven
archetype. Move to your Eclipse workspace and perform :

-   `mvn archetype:generate
              -DarchetypeCatalog=http://repository.jspresso.org/maven2/`

And choose the “Jspresso Application Archetype”.

Then fill-in the questions with the following answers :

-   “groupId” : `org.jspresso.hrsample`

-   “artifactId” : `hrsample`

-   “package” : `org.jspresso.hrsample`

-   “version” : `1.0-SNAPSHOT`

This will generate a complete project ready to be compiled and packaged
under the `hrsample/` directory. So move to the generated directory and
type :

-   `mvn package`

The operation may take some time to finish since Maven will download all
the needed plugins and dependencies in its local repository. Just wait
for the “BUILD SUCCESSFUL” message and you should have a packaged
`hrsample-webapp.war` in the `hrsample/webapp/target/` directory.

Importing the project in Eclipse
--------------------------------

Follow the [installation steps](???) described on the Jspresso site and
then import the project skeleton you've generated using the M2Eclipse
project import wizard.

The development environment is now set-up. We can begin the Human
Resources sample application coding.

The human resources (HR) sample application
===========================================

The human resources application is a simple yet comprehensive business
application targeted at managing a company organization and the
employees who work in it. It will demonstrate how Jspresso can handle a
domain model with its relationships and its constraints, present it to
the end-user for manipulation through various built-in views and
actions, handle security through profile management, distribute the
frontend across the network, ...

The domain model
----------------

To quickly introduce the HR domain model, let's dive into the following
UML class diagrams. As a general rule to make the diagrams more
readable, attributes must be considered as getter / setter pairs.

