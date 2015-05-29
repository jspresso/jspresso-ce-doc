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

The application workspaces
--------------------------

The HR application is divided in 3 workspaces.

### The organization management workspace

This workspace manages a company structure in terms of organizational
units. The end-user may create/delete/update a company,
create/delete/update its organizational units and structure them in the
organization. The end-user may compose the employee teams, assign an
organisational unit manager but won't be able to create/update/delete an
employee. The organization must be displayed in a hierarchical (tree)
view.

### The employees management module

This workspace manages a company staff. The end-user can retrieve the
company employees and create/update/delete an employee.

### The master data management module

This module manages the application master data. As of now, the master
data are only made of the cities available to compose the addresses.

The profiles
------------

The HR application offers 3 profiles.

### The organization manager profile

A logged-in user having the organization manager profile will be granted
access to the organization management workspace as well as the master
data management workspace but he won't be able to access the employee
management workspace.

### The staff manager profile

A logged-in user having the staff manager profile will be granted access
to the employee management workspace as well as the master data
management workspace but he won't be able to access the organization
management workspace.

### The administrator profile

The administrator profile has no restriction in the application.

Layering the application
========================

Now that we have collected the detailed specifications, it's time to
feed the framework with them. As we saw before, most of the job will
consist in describing the different layers in a structured way. But
before going further, let's define the best practices regarding the
logical layering of a typical Jspresso application (although these
practices may generally apply to any well designed application). We will
define 3 logical layers from the bottom to the top :

-   The domain model

-   The backend

-   The frontend

This organisation will help to prevent cyclic dependencies between
layers since each layer will be allowed to use lower ones but not higher
ones (e.g. : the backend may use the domain model but not the frontend).

Of course, this is a minimal logical layering. Each of this layer may be
further divided in subparts depending on the software complexity. For
instance the domain model might be divided in master and movement data
and the backend and frontend may be divided in modules. It's entirely up
to the application designer to tailor these rules. But it surely is the
first design activity.

The [general architecture diagram](#general-cod) introduces this
layering strategy.

![General architecture diagram](../uml/general-cod.PNG)

Let's define now what precisely go in these layers.

The domain model
----------------

The domain model includes :

-   The entities. An entity will be described by :

    -   properties along with their constraints and their interceptors

    -   behaviour (business methods, life-cycle interceptors)

    -   integrity enforcements

    -   default presentation elements (name, icon, rendered properties,
        ordering properties)

    -   relationships to other entities (cardinality, reversibility)

-   The components. A component has all the characteristics of an entity
    except that it is not autonomous since It is designed as a structure
    to be inlined in an entity (e.g. : an address structure).

-   Other structural elements like common business interfaces.

We will see later that there virtually any domain model can be
extensively described using Jspresso. This includes for instance
polymorphic entities or associations, multiple inheritance, and so on.

The backend
-----------

The backend includes all the application parts that do not depend on the
client :

-   The actions server parts (which interact with the domain model for
    instance)

-   The application workspaces along with their hierarchy of modules. A
    workspace is a top application entry point which is directly
    accessible by the end user.

-   The application modules. They form a hierarchy since modules may
    contain other modules. Each module is an independent application
    part targeted at accessing the backend data (domain model
    manipulation, reporting, ...).

-   The backend controller which holds the user backend application
    state and its configuration (in-memory model state)

The frontend
------------

The frontend includes all the application parts that interact directly
with the end-user :

-   The views

-   The action client parts (which handle user interaction and trigger
    action server parts)

-   The client application module parts

-   The frontend controller which holds the user frontend application
    state and its configuration (workspaces and modules state)

Describing the domain model
===========================

In this chapter, you will learn how to feed the Jspresso framework with
the sample domain model description.

Using the "Sugar for Jspresso" DSL
----------------------------------

The preferred way of writing applications is to use the new Jspresso
Groovy based DSL (Domain Specific Language) : "Sugar for Jspresso" - aka
**SJS**. The SJS DSL was thought from the very begining to stay
compatible with Spring XML which was the legacy language used in
Jspresso. This means that during the build, the SJS authored files are
"compiled" to generate Spring XML files that are loaded in the Spring
context beside the legacy ones. So you can :

-   develop only using SJS.

-   develop only using Spring XML.

-   develop using SJS and Spring XML and even reference on one side,
    components that are defined on the other side.

For instance, describing your application model will be a matter of
writing SJS code into the `model.groovy` file located here :

> `hrsample/core/src/main/dsl/model.groovy`

Authoring SJS code is greatly simplified when using [Jspresso Developer
Studio](http://www.jspresso.org/page/jspresso-developer-studio), so make
sure you've correctly installed it.

Here is what the default generated `model.groovy` looks like :

``` {.xml}
// Implement your domain here using the SJS DSL.
 
```

> **Note**
>
> For those who are familiar with Jspresso Spring XML, and want to
> migrate smoothly to SJS, you can always have a look to the SJS
> generated Spring config files. For instance, `model.groovy` will be
> translated into
> `hrsample/core/target/generated-resources/dsl/org/jspresso/hrsample/model/dsl-model.xml`
> by the SJS compiler.

In all example given using the SJS DSL, pay special attention to
conventions. For instance, package names are most of the time inferred
and you will rarely change the default. This feature makes SJS code much
more compact and easier to read than plain Spring XML.

Interfaces
----------

As a starting point, we will describe the [commons](#commons-cd) model
part.

The `Nameable` interface may be described as follow :

``` {.groovy}
Interface ('Nameable') {
  string_64 'name', mandatory:true
}
```

Since we are describing a generic interface (which may or may not turn
to be an entity) we will use an `Interface` keyword. We name the
interface ``. By convention, since we are in the org.jspresso.hrsample
namespace, this will turn into a org.jspresso.hrsample.model.Nameable
interface class. We declare a String property, with a maximum length of
64 chars. We name this property `name`, so that the corresponding
`getName()` and `setName(String)` accessors will be generated. We make
this property mandatory.

As you can see above, we create an interface descriptor
(`org.jspresso.hrsample.model.Nameable`) with one property (`name`)
along with its constraints (`maxLength` and `mandatory`). This is a
fairly simple interface since it has no intrinsic behaviour nor
relationships with other components.

So now, lets describe the `Traceable` interface as follow :

``` {.groovy}
Interface('Traceable',
          uncloned:['createTimestamp', 'lastUpdateTimestamp']) {
  date_time 'createTimestamp', readOnly:true, timeZoneAware:true
  date_time 'lastUpdateTimestamp', readOnly:true, timeZoneAware:true
}
```

Whenever an entity implementing the Traceable interface is cloned by
Jspresso, the cloning process will ignore both tracing properties. We
declare a date property for which the time portion will be preserved.
The date property is made read-only, i.e. it will only be updated
programatically. The date property is a technical date, i.e. it is
sensitive to the client / server timezones difference. It will translate
differently depending on the client timezone.The `Traceable` interface
description is slightly more complicated than the `Nameable` interface
since not all properties are eligible to cloning (`uncloned`).

Generating the domain model code
--------------------------------

It is time now to get our interfaces generated before going further.
Let's use the Jspresso generation tool to make it happen.

As we saw before the Jspresso build is completely integrated in Maven.
This includes domain model code generation. You can trigger the build
from an external terminal window or directly from the IDE using an maven
Eclipse plugin. Navigate to your project root folder and type :

> `mvn compile`

> **Note**
>
> If you want to speed up this generation phase, instead of launching
> `mvn compile` from the `hrsample/` root folder, you can lauch it from
> the `hrsample/core/` folder which is the project module that holds the
> domain model.

Go back to Eclipse and refresh your project - F5 - so that the generated
java source is detected. You may now have a look to the following folder
to see the generated java source files :

> `hrsample/core/target/generated-sources/entitygenerator/org/jspresso/hrsample/model`

Alternatively you can directly use the Eclipse “Open type” function to
Quickly navigate navigate to the generated `Nameable` and `Traceable`
types.

> **Note**
>
> Jpresso uses compile time generation of the domain model classes and
> resources. Generated artifacts always go into `target/generated-xxx`
> folders. You should never place any hand-written code in these
> generated source folders since they can be deleted at any time during
> a `maven clean` operation. Always use standard maven source folders
> (`src/main/java` and `src/main/resources`).

You should have now the 2 generated classes :

-   `Nameable.java` for the Nameable interface (see the [source code
    below](#Nameable)).

-   `Traceable.java` for the Traceable interface.

``` {#Nameable .java}
package org.jspresso.hrsample.model;

/**
 * Nameable component.
 * <p>
 * Generated by Jspresso. All rights reserved.
 * <p>
 *
 * @author Generated by Jspresso
 */
public interface Nameable {

  /**
   * Gets the name.
   *
   * @hibernate.property
   * @hibernate.column
   *           name = "NAME"
   *           length = "64"
   *           not-null = "true"
   * @return the name.
   */
  java.lang.String getName();

  /**
   * Sets the name.
   *
   * @param name
   *          the name to set.
   */
  void setName(java.lang.String name);

}
```

These 2 java classes are actually java interfaces with getters and
setters for the declared properties. In fact, you will never need any
implementation for them since Jspresso will automatically handle their
implementation for you at runtime using J2SE proxies. This approach
relieves the developer from writing the implementation classes and thus,
improves quality, robustness and productivity.

You may also notice that the generator took care of annotating the
classes with [hibernate](http://www.hibernate.org/)
[xDoclet](http://xdoclet.sourceforge.net/xdoclet/index.html) attributes.
They will be used later to generate the necessary persistence meta-data.

Adding life-cycle behaviour
---------------------------

What about the handling of the `Traceable` properties ? We want them to
follow the life-cycle of any traceable entity, i.e. :

-   Set the `createTimestamp` when the entity is persisted for the first
    time.

-   Set the `lastUpdateTimestamp` when the entity is updated in the
    persistent store.

It is time to write our first lines of java to achieve that. Navigate to
the `/hrsample/core/src/main/java` source folder and create the
life-cycle interceptor
`org.jspresso.hrsample.model.service.TraceableLifecycleInterceptor` java
class as follow :

``` {.java}
package org.jspresso.hrsample.model.service;

import java.util.Date;

import org.jspresso.hrsample.model.Traceable;
import org.jspresso.framework.model.component.service.EmptyLifecycleInterceptor;
import org.jspresso.framework.model.entity.IEntityFactory;
import org.jspresso.framework.model.entity.IEntityLifecycleHandler;
import org.jspresso.framework.security.UserPrincipal;

/**
 * Default lifecycle service for tracing.
 */
public class TraceableLifecycleInterceptor extends
    EmptyLifecycleInterceptor<Traceable>  {

  /**
   * Sets the create timestamp.
   * <p>
   * {@inheritDoc}
   */
  @Override
  public boolean onPersist(Traceable traceable, IEntityFactory entityFactory,
      UserPrincipal principal, IEntityLifecycleHandler entityLifecycleHandler) {
    traceable.setCreateTimestamp(new Date()); 
    return true; 
  }

  /**
   * Sets the last update timestamp.
   * <p>
   * {@inheritDoc}
   */
  @Override
  public boolean onUpdate(Traceable traceable, IEntityFactory entityFactory,
      UserPrincipal principal, IEntityLifecycleHandler entityLifecycleHandler) {
    traceable.setLastUpdateTimestamp(new Date()); 
    return true;
  }
}
```

The class inherits from the support class `EmptyLifecycleInterceptor`
which empty implements the required life-cycle interceptor interface
`EmptyLifecycleInterceptor` as well as the marker interface
`IComponentService`.

Whenever a `Traceable` component is persisted (saved for the first
time), set its `createTimestamp`.

Return true to notify the framework that the state of the component has
been updated.

Whenever a `Traceable` component is updated (subsequent saves), update
its `lastUpdateTimestamp`.

We can now link the life-cycle interceptor to our `Traceable` interface
bean descriptor as below :

``` {.groovy}
Interface('Traceable',
    ,
    uncloned:['createTimestamp', 'lastUpdateTimestamp']) {
  ...
}
```

Defines an ordered list of life-cycle interceptors attached to the
component. Note that, by convention, we can ommit the package of the
TraceableLifecycleInterceptor class, since it will be inferred from the
current namespace.

Entities
--------

As of now, we have only dealt with interfaces which are not entities by
themselves. Describing an entity follows the exact same process except
that we make its descriptor an entity descriptor.

So let's describe the `City` entity as below :

``` {.groovy}
Entity('City',
       extend:'Nameable') {
  string_10 'zip'
}
```

We are now declaring a concrete entity, thus using the `Entity` keyword.
We make the `` entity inherit from the `` interface, so it will bring
the name property.

the Jspresso Maven compilation will produce the following class
(`City.java`) :

``` {.java}
package org.jspresso.hrsample.model;

/**
 * City entity.
 * <p>
 * Generated by Jspresso. All rights reserved.
 * <p>
 *
 * @hibernate.mapping
 *           default-access = "org.jspresso.framework.model.persistence\
 *                             .hibernate.property.EntityPropertyAccessor"
 * @hibernate.class
 *   table = "CITY"
 *   dynamic-insert = "true"
 *   dynamic-update = "true"
 *   persister = "org.jspresso.framework.model.persistence.hibernate.entity\
 *                .persister.EntityProxyJoinedSubclassEntityPersister"
 * @author Generated by Jspresso
 */
public interface City extends
  org.jspresso.hrsample.model.Nameable,
  org.jspresso.framework.model.entity.IEntity  {

  /**
   * @hibernate.id generator-class = "assigned" column = "ID" type = "string"
   *               length = "36"
   * <p>
   * {@inheritDoc}
   */
  java.io.Serializable getId();

  /**
   * @hibernate.version column = "VERSION" unsaved-value = "null"
   * <p>
   * {@inheritDoc}
   */
  Integer getVersion();

  /**
   * Gets the zip.
   *
   * @hibernate.property
   * @hibernate.column
   *           name = "ZIP"
   *           length = "10"
   * @return the zip.
   */
  java.lang.String getZip();

  /**
   * Sets the zip.
   *
   * @param zip
   *          the zip to set.
   */
  void setZip(java.lang.String zip);

}
```

`City` is an entity so the generator made it inherit from `IEntity`
which is a Jspresso framework base class.

You might notice that there are slightly more hibernate xDoclet tags
(class level tags, id and version) to handle the entity persistence
specifics. But as for `Nameable` and `Traceable`, the `City` entity is
not more than an interface and its implementation will be completely
handled by the framework.

Components
----------

A component is a data structure which is intended to be inlined in other
components or entities. Like entities and interfaces, you can define
properties and behaviour in a component. A component cannot live by
itself. It is an elegant mean to factor common data and behaviour into
higher level model parts.

So let's describe the `ContactInfo` component as below :

``` {.groovy}
Component('ContactInfo') {
  string_256 'address'
  string_32  'phone'
  string_128 'email', regex:"[\\w\\-\\.]*@[\\w\\-\\.]*", regexSample:'contact@acme.com'
}
```

Since `ContactInfo` is an component, we use a `Component` keyword. This
is a special kind of string constraint enforcement through a regular
expression; we want an email to conform to contain the @ sign, be
without space and be only composed of literals plus '.' and '-'.
Whenever there is some kind of communication to initiate (an invalid
value for instance), this is an example of a correct value.

Relaunching the Jspresso generator will produce the following class
(`ContactInfo.java`) :

``` {.java}
package org.jspresso.hrsample.model;

/**
 * ContactInfo component.
 * <p>
 * Generated by Jspresso. All rights reserved.
 * <p>
 *
 * @author Generated by Jspresso
 */
public interface ContactInfo extends
  org.jspresso.framework.model.component.IComponent  {

  /**
   * Gets the address.
   *
   * @hibernate.property
   * @hibernate.column
   *           name = "ADDRESS"
   *           length = "256"
   * @return the address.
   */
  java.lang.String getAddress();

  /**
   * Sets the address.
   *
   * @param address
   *          the address to set.
   */
  void setAddress(java.lang.String address);

  /**
   * Gets the phone.
   *
   * @hibernate.property
   * @hibernate.column
   *           name = "PHONE"
   *           length = "32"
   * @return the phone.
   */
  java.lang.String getPhone();

  /**
   * Sets the phone.
   *
   * @param phone
   *          the phone to set.
   */
  void setPhone(java.lang.String phone);

  /**
   * Gets the email.
   *
   * @hibernate.property
   * @hibernate.column
   *           name = "EMAIL"
   *           length = "128"
   * @return the email.
   */
  java.lang.String getEmail();

  /**
   * Sets the email.
   *
   * @param email
   *          the email to set.
   */
  void setEmail(java.lang.String email);

}
```

`ContactInfo` is an entity so the generator made it inherit from
`IComponent` which is a Jspresso framework base class.

You might have notice that the `ContactInfo` component is missing
something : its relationship to the `City` entity.

Unidirectional relationships
----------------------------

It's time to link our first components together.

### Unidirectional N-1 relationships

Let's first deal with the simple unidirectional association
`ContactInfo` -\> `City`. We are going to define a `city` property in
the `ContactInfo` component.

The following SJS fragment will do the trick :

``` {.groovy}
Component('ContactInfo') {
  ...
  
  ...
}
```

`ContactInfo` has a reference to the `City` entity so we describe this
using a `reference` keyword. We link the reference property to the
`City` entity we described above.

Relaunching the Maven compilation will update the `ContactInfo.java`
source file we generated above, but since this is a unidirectional
relationship, the `City.java` file will remain untouched. The following
lines are added in the `ContactInfo.java` source file :

``` {.java}
  /**
   * Gets the city.
   *
   * @hibernate.many-to-one
   *           cascade = "persist,merge,save-update,refresh,evict,replicate"
   * @hibernate.column
   *           name = "CITY_ID"
   * @return the city.
   */
  org.jspresso.hrsample.model.City getCity();

  /**
   * Sets the city.
   *
   * @param city
   *          the city to set.
   */
  void setCity(org.jspresso.hrsample.model.City city);
```

Again, the needed hibernate xDoclet tags are added to reflect the
relationship between the component and the entity.

To end with the commons model part, let's define the Event entity :

``` {.groovy}
Entity('Event',extend:'Traceable'){
  html 'text', maxLength:2048 , id:'Event-text'
}
```

An event is a `Traceable` entity. We use a `html` property instead of a
`string` one. This is to inform the framework that this property is used
to store HTML formatted data; although there is no direct impact on the
model layer (it is still stored as a `String`), it might be useful in
the view layer (e.g. : use a rich text area instead of a text field to
display and edit the `Event` text property). We assign explicitely an id
to the `text` property. This is to be able to reference it individually
from another layer (e.g. the view layer). By default, only reference and
collection properties are implicitly assigned an id in the form
`Owner-property`. We kept this convention to declare an id on the text
property.

This first relationship is fairly simple since it is a n-1
unidirectional association. Of course, the Jspresso can also seamlessly
handle 1-n, 1-1 and n-n unidirectional and bi-directional associations
and compositions (strong aggregations).

Now that we are done with the commons model part, let's see how we can
handle the employees model part.

### Inlined components

The `Employee` entity is fairly simple to describe giving what we
already achieved.

Let's look at the SJS code below :

``` {.groovy}
Entity ('Employee',
        extend:['Nameable','Traceable']) {
  string_32 'firstName', mandatory:true
  string_10 'ssn', regex:'[\\d]{10}', regexSample:'0123456789', unicityScope:'empSsn'
  date 'birthDate'
  date 'hireDate'
  enumeration 'gender', enumName:'GENDER', mandatory:true, valuesAndIcons:[
              'M':'male-48x48.png',
              'F':'female-48x48.png']
  color 'preferredColor'
  bool 'married'
  decimal 'salary', minValue:0
  binary 'photo', maxLength:1048576, id:'Employee-photo',
         fileFilter:['images':['.jpg']],
         fileName:'photo.jpg'
  password 'password', maxLength:32
  reference 'contact', ref:'ContactInfo', id:'contact'
}
```

We defined a regular expression control on the ssn property since it
must be composed of 10 and only 10 digits. We define a unicity domain
for the `ssn` property. This will translate in a unique key definition
in the persistent store. We don't care about the time information of
this date; so we use a `date` keyword as opposed to the `date_time`
keyword that we used for the `Traceable` interface. This is a new type
of property. This one defines a finite choice of values. We define each
of the values composing the choice for the gender enumeration (either
'M' or 'F') along with icons if available. This defines a color
property. Color properties are internally stored as their RGBA base 16
encoded value, but are visualized and edited using a color chooser un
the UI. This defines a boolean property. This defines a decimal
property. This defines a binary property. It comes with a file filter to
set up the file extensions that are to be configured when the user
chooses a file to upload in order to fill in this property value as well
as a default filename that is used whensaving the property content to a
file. This defines a password property. It is stored internally as a
string but is visually represented using a password field. This is where
we reference the `ContactInfo` component.

The employee description above shows that it is strictly equivalent - as
far as description is concerned - to reference an entity or to inline a
component (see the contact reference). The difference will be in the
persistence store and in the views since an inlined component will have
its attributes "merged" with the enclosing component as if they belonged
to it.

### Unidirectional 1-N relationships

You have surely noticed that we did not describe the 1-N composition
between `Employee` and `Event`. This will be our first collection
property and its description is actually quite straightforward :

And the SJS way (note that SJS will automatically generate a top-level
bean for the collection property, with an id in the form of
*Owner-property*, i.e. *Employee-events*) :

``` {.groovy}
Entity ('Employee'...) {
  ...
  list 'events', composition:true, ref:'Event'
  ...
}
```

We are describing a collection relationship property. Since we want an
arbitrary, persistent, order using an index, we declare it as a `list`.
If we didn't want to actually persist an arbitrary order (which is the
vast majority of the cases), we would have used a `set` semantic using
the `set` keyword. We make this relationship a composition to express
the fact that whenever an employee is deleted, the attached events must
also be deleted. Our collection property lists events; so we reference
the `Event` entity as being the element type of our collection.

> **Note**
>
> SJS automatically generates an automatic id for collection properties
> and for reference properties. The generated id has the form of
> *Owner-property*, i.e. *Employee-events*

Launching the Jspresso generator will generate the `Employee.java`
source file :

``` {.java}
package org.jspresso.hrsample.model;

/**
 * Employee entity.
 * <p>
 * Generated by Jspresso. All rights reserved.
 * <p>
 *
 * @hibernate.mapping default-access =
 *                    "org.jspresso.framework.model.persistence\
 *                     .hibernate.property.EntityPropertyAccessor"
 * @hibernate.class table = "EMPLOYEE"
 *   dynamic-insert = "true"
 *   dynamic-update = "true"
 *   persister = "org.jspresso.framework.model.persistence.hibernate.entity\
 *                .persister.EntityProxyJoinedSubclassEntityPersister"
 * @author Generated by Jspresso
 */
public interface Employee extends org.jspresso.hrsample.model.Nameable,
    org.jspresso.hrsample.model.Traceable,
    org.jspresso.framework.model.entity.IEntity {

  /**
   * @hibernate.id generator-class = "assigned" column = "ID" type = "string"
   *               length = "36"
   *               <p>
   *               {@inheritDoc}
   */
  java.io.Serializable getId();

  /**
   * @hibernate.version column = "VERSION" unsaved-value = "null"
   *                    <p>
   *                    {@inheritDoc}
   */
  Integer getVersion();

  /**
   * Gets the firstName.
   *
   * @hibernate.property
   * @hibernate.column name = "FIRST_NAME" length = "32"
   * @return the firstName.
   */
  java.lang.String getFirstName();

  /**
   * Sets the firstName.
   *
   * @param firstName
   *            the firstName to set.
   */
  void setFirstName(java.lang.String firstName);

  /**
   * Gets the ssn.
   *
   * @hibernate.property
   * @hibernate.column name = "SSN" length = "10" unique-key = "EMP_SSN_UNQ"
   * @return the ssn.
   */
  java.lang.String getSsn();

  /**
   * Sets the ssn.
   *
   * @param ssn
   *            the ssn to set.
   */
  void setSsn(java.lang.String ssn);

  /**
   * Gets the birthDate.
   *
   * @hibernate.property type = "date"
   * @hibernate.column name = "BIRTH_DATE"
   * @return the birthDate.
   */
  java.util.Date getBirthDate();

  /**
   * Sets the birthDate.
   *
   * @param birthDate
   *            the birthDate to set.
   */
  void setBirthDate(java.util.Date birthDate);

  /**
   * Gets the hireDate.
   *
   * @hibernate.property type = "date"
   * @hibernate.column name = "HIRE_DATE"
   * @return the hireDate.
   */
  java.util.Date getHireDate();

  /**
   * Sets the hireDate.
   *
   * @param hireDate
   *            the hireDate to set.
   */
  void setHireDate(java.util.Date hireDate);

  /**
   * Gets the gender.
   *
   * @hibernate.property
   * @hibernate.column name = "GENDER" length = "1" not-null = "true"
   * @return the gender.
   */
  java.lang.String getGender();

  /**
   * Sets the gender.
   *
   * @param gender
   *            the gender to set.
   */
  void setGender(java.lang.String gender);

  /**
   * Gets the contact.
   *
   * @hibernate.component prefix = "CONTACT_"
   * @return the contact.
   */
  org.jspresso.hrsample.model.ContactInfo getContact();

  /**
   * Gets the preferredColor.
   *
   * @hibernate.property
   * @hibernate.column
   *           name = "PREFERRED_COLOR"
   *           length = "10"
   * @return the preferredColor.
   */
  java.lang.String getPreferredColor();

  /**
   * Sets the preferredColor.
   *
   * @param preferredColor
   *          the preferredColor to set.
   */
  void setPreferredColor(java.lang.String preferredColor);

  /**
   * Gets the married.
   *
   * @hibernate.property
   * @hibernate.column
   *           name = "MARRIED"
   *           not-null = "true"
   * @return the married.
   */
  boolean isMarried();

  /**
   * Sets the married.
   *
   * @param married
   *          the married to set.
   */
  void setMarried(boolean married);

  /**
   * Gets the salary.
   *
   * @hibernate.property
   * @hibernate.column
   *           name = "SALARY"
   *           precision = "10"
   *           scale = "2"
   * @return the salary.
   */
  java.math.BigDecimal getSalary();

  /**
   * Sets the salary.
   *
   * @param salary
   *          the salary to set.
   */
  void setSalary(java.math.BigDecimal salary);

  /**
   * Gets the photo.
   *
   * @hibernate.property
   * @hibernate.column
   *           name = "PHOTO"
   *           length = "1048576"
   * @return the photo.
   */
  byte[] getPhoto();

  /**
   * Sets the photo.
   *
   * @param photo
   *          the photo to set.
   */
  void setPhoto(byte[] photo);

  /**
   * Gets the password.
   *
   * @hibernate.property
   * @hibernate.column
   *           name = "PASSWORD"
   *           length = "32"
   * @return the password.
   */
  java.lang.String getPassword();

  /**
   * Sets the password.
   *
   * @param password
   *          the password to set.
   */
  void setPassword(java.lang.String password);

  /**
   * Sets the contact.
   *
   * @param contact
   *            the contact to set.
   */
  void setContact(org.jspresso.hrsample.model.ContactInfo contact);

  /**
   * Gets the events.
   *
   * @hibernate.list cascade =
   *                 "persist,merge,save-update,refresh,evict,replicate,delete"
   * @hibernate.key column = "EVENTS_EMPLOYEE_ID"
   * @hibernate.one-to-many class = "org.jspresso.hrsample.model.Event"
   * @hibernate.list-index column = "EVENTS_SEQ"
   * @return the events.
   */
  java.util.List<org.jspresso.hrsample.model.Event> getEvents();

  /**
   * Sets the events.
   *
   * @param events
   *            the events to set.
   */
  void setEvents(java.util.List<org.jspresso.hrsample.model.Event> events);

  /**
   * Adds an element to the events.
   *
   * @param eventsElement
   *            the events element to add.
   */
  void addToEvents(org.jspresso.hrsample.model.Event eventsElement);

  /**
   * Adds an element to the events at the specified index. If the index is out
   * of the list bounds, the element is simply added at the end of the list.
   *
   * @param index
   *            the index to add the events element at.
   * @param eventsElement
   *            the events element to add.
   */
  void addToEvents(int index,
      org.jspresso.hrsample.model.Event eventsElement);

  /**
   * Removes an element from the events.
   *
   * @param eventsElement
   *            the events element to remove.
   */
  void removeFromEvents(org.jspresso.hrsample.model.Event eventsElement);

}
```

As you can see above, the generator has generated all the accessors for
the events list property. If the events property had been designed as a
set instead of a list, the adder using the index would not have been
generated and the get/set pair would of course have used a
`java.util.Set` instead of a `java.util.List`.

Now that the employees model part is complete, let's deal with the
organization.

Entity inheritance
------------------

The organization model part is the most complex of the example, since it
involves entity inheritance (and polymorphism) and other kinds of
relationships (1-1, bi-directional). So let's begin with the entity
inheritance graph and we will deal with their relationships next :

``` {.groovy}
Entity('Company',
       extend:['Nameable', 'Traceable']) {
  reference 'contact', ref:'ContactInfo'
}

Entity('OrganizationalUnit',
       extend:['Nameable', 'Traceable'],
       purelyAbstract:true) {
  string_6 'ouId', regex:"[A-Z]{2}-[\\d]{3}", regexSample:'AB-123', mandatory:true
  reference 'contact', ref:'ContactInfo'
}

Entity('Department',
       extend:'OrganizationalUnit')

Entity('Team',
       extend:['OrganizationalUnit'])
```

An `OrganizationalUnit` will never be instantiated as such; only
sub-entities will. This is why we define the entity as purely abstract.
`Department` inherits from `OrganizationalUnit` as do `Team`.

Pretty easy, no ? You describe entity inheritance exactly as you did
previously for the interfaces. You don't have to care for anything else,
the framework will handle it behind the scene for you.

You can see also that `Company`, `OrganizationalUnit`, and `Employee`
have the same contact property as an inlined `ContactInfo` component. It
is a perfect candidate for factoring. So we can make the contact
property descriptor a top level reference, name it contact and reference
it in the 3 entities above. The result will be :

``` {.groovy}
Entity('Employee'...) {
  ...
  reference 'contact', ref:'ContactInfo', 
  ...
}

Entity('Company'...) {
  ...
  
  ...
}

Entity('OrganizationalUnit'...) {
  ...
  
  ...
}
```

We factor the contact property in a top level referenceable element
named "contact". We reference the contact bean as a property of the
`Company` entity We reference the contact bean as a property of the
`OrganizationalUnit` abstract entity.

Now that we have described our organization entities, let's link them
together using relationships.

Bi-directional relationships
----------------------------

It is time see how the Jspresso framework handles relationships that are
navigable at both ends.

### Bi-directional 1-N relationships

We are going to describe the `Company` \<-\> `Department` bi-directional
1-N relationship. To achieve that, we will first describe the N side of
this composition, making it a top-level, referenceable bean and then
make this N side the reverse end of the 1 side of the composition. This
is achieved using the following SJS fragment :

``` {.groovy}
Entity('Company'...) {
  ...
  set 'departments', composition:true, ref:'Department'
}

Entity('Department'...) {
  ...
  reference 'company', ref:'Company', , mandatory:true
}
```

Like we did before for the employee `events`, we describe collection
property for the company `departments`. This time, the collection
property has a set semantic. We link both side of the `Company` \<-\>
`Department` relationship assigning 1 side reverse of the other.

So making a relationship bi-directional is quite straightforward. We
just have to reference one end of the relationship in the other end as
being the reverse end. Although the generated java code will not be
directly impacted by making a relationship bi-directional, hibernate
xDoclet tags will be. More important is the impact on how the framework
will handle the relationship updates behind the scene for you.

Making the `Company` \<-\> `Department` relationship bi-directional
implies the following on the `Company` side:

1.  Whenever a department is added to a company through the
    `addToDepartments(Department)` adder, the passed-in department will
    have its company property updated accordingly. In the (unexpected)
    case that the department was part of another company, it will be
    removed from its previous company departments before being added to
    the new one.

2.  Whenever a set of departments set as the company departments through
    the `setDepartments(Set<Department>)` setter, all the passed-in
    departments will have their company property updated accordingly. In
    the (unexpected) case that the departments were part of other
    companies, they will be removed from their previous respective
    company departments before being added to the new one. Moreover, all
    existing departments in the company before the update will have
    their company property reset.

3.  Whenever a department is removed from a company through the
    `removeFromDepartments(Department)` remover, the passed-in
    department will have its company property reset to `null`. In the
    (unexpected) case that the department was part of another company,
    it will be removed from its previous company departments.

And on the `Department` side :

1.  Whenever a company is set in a department through the
    `setCompany(Company)`, the company departments is updated
    accordingly. In the case that the passed-in company is `null`, the
    department will just be removed from its previous company if any.

As you can see above, you can expect the Jspresso framework to
extensively and transparently manage any bi-directional relationship for
you. Just call whatever accessor you want and the domain model will be
updated consistently.

We describe the `Department` \<-\> `Team` relationship the same way :

``` {.groovy}
Entity('Department'...) {
  ...
  set 'teams', composition:true, ref:'Team'
}

Entity('Team'...) {
  reference 'department', ref:'Department', reverse:'Department-teams', mandatory:true
}
```

And, to be complete, the `Company` \<-\> `Employees` relationship :

``` {.groovy}
Entity('Company'...) {
  ...
  set 'employees', composition:true, ref:'Employee'
}

Entity('Employee'...) {
  reference 'company', ref:'Company', reverse:'Company-employees', mandatory:true
}
```

