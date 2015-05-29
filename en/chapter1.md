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

The [commons class diagram](#commons-cd) describes commonly used
interfaces and classes.

A few hints :

-   The traceable interface is implemented by entities for which we need
    to record when it was saved for the first time and when it was last
    updated. Of course, these tracing elements must be made read-only to
    the end-user since they are automatically managed by the
    application.

-   The nameable is implemented by entities having a name. A name has a
    max length of 64 characters and is mandatory. Nameable implements a
    service which formats its name (a really simple service only for
    demonstration purpose).

-   The contact information component is used by entities that have
    contact details (address, phone, email, ...). A contact information
    points to one and only one city. A city is nameable and has a zip
    code of maximum length 10 characters.

-   An event is a piece of text which is traceable

![Commons class diagram](../uml/commons-cd.PNG)

The [employees class diagram](#employee-cd) describes what an employee
is.

A few hints :

-   An employee is nameable and traceable. An employee has :

    -   a first name (his last name is inherited by the nameable
        interface)

    -   a social security number which is composed by exactly 10 digits
        and which is unique among all employees

    -   a gender (male or female)

    -   a birth date

    -   a hire date in the company

    -   a contact information

    -   a preferred color

    -   a flag indicating if (s)he is married

    -   a salary

    -   a photo

-   An employee must provide a method to compute his age based on his
    birth date.

-   An employee has an ordered list of events.

![Employees class diagram](../uml/employees-cd.PNG)

The [organization class diagram](#organization-cd) describes how the
company is structured in departments and teams.

A few hints :

-   A company is structured in organizational units. An organizational
    unit may be a department or a team. An organizational unit has an
    identifier (*ouId*) which is formed by a 2 letter code followed by a
    dash followed by a 3 digit number (*IS-001* for instance). Each
    organizational unit has a manager who is an employee of the company
    it belongs to. An employee can at most manage one organizational
    unit. An organizational unit is nameable, traceable and has contact
    information as well as a company has.

-   The company may have one or more departments and a department
    belongs to one and only one company.

-   A department may have one or more teams and a team belongs to one
    and only one department. Each team is composed by one or more
    employees.

-   An employee belongs to one and only one company. An employee may
    belong to zero or more teams.

![Organization class diagram](../uml/organization-cd.PNG)

