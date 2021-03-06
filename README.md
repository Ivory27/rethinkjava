rethinkjava
===========

Java/JVM Drivers for RethinkDB ( rethinkdb.com )


# Status 
This drivers are being worked on now and is currently in progress. I make no claims about the usability, stability, or safety of this code. 

This driver is working with API version 1.0 ( RethinkDB 1.5, 1.6, 1.7 ) 

## Changelog 

* 0.1 (June 2012) Initial push of project and first support for Maven
* 0.2 (June 2012) Added the rest of the Rql language to driver and provided method to deconstruct responces.
* 0.3 (July 2012) Fixed Errors in Datum Encoding and RqlCursors. Added More testing
* 0.4 (July 2012) Added the instance methods so API looks much like the python API. Further testing added. 

## Using rethinkjava 
Add the following to your pom.xml
```xml
<repository>
    <id>rethinkjava-mvn-repo</id>
    <url>https://raw.github.com/dkhenry/rethinkjava/mvn-repo/</url>
    <snapshots>
        <enabled>true</enabled>
        <updatePolicy>always</updatePolicy>
    </snapshots>
</repository>

```

Then in your dependencides section add the following 
```xml
<dependency>
    <groupId>com.dkhenry</groupId>
    <artifactId>rethinkjava</artifactId>
    <version>0.1</version>
  </dependency>
```

## Whats Working 
Connecting, Reading, and Writing work as expected ( mostly ) 

Also The Database administration querys should be working ( db_create, db_drop, db_list, table_create, table_drop, table_list )

##Whats not working 
Authentication in the API 

Using functions as arguments in any part of the API

Actualy testing of everything

Formal Examples. 

# How you can Help 
Make the testing better ( This is actually really important ) 

Fork the repo and make pull requests 

Submit defects and feature request 

Create some kind of documentation ( java docs on all the instance methods would be awesome ) 

Converting the instance methods to actually take in parmaters ( this will help in finding compile time defects, and documentation )

# Planned API 
I want to keep this API as close to the official API's as I can. This is an example of what I will try to accomplish


    RethinkDB r = RethinkDB.connect(hostname,port);
    // Any use of db set the default db
    r.db("test").table_create("characters");
    // A simple Insert
    r.db("test").table("characters").insert(Arrays.asList(
				    new HashMap() {{ put("name","Worf");put("show","Star Trek TNG"); }},
				    new HashMap() {{ put("name","Data");put("show","Star Trek TNG"); }},
				    new HashMap() {{ put("name","William Adama");put("show","Battlestar Galactica"); }}, 
				    new HashMap() {{ put("name","Homer Simpson");put("show","The Simpsons"); }}
				));

    // Then a Simple Query
    r.table("tv_shows")
	  .filter(new HashMap() {{ put("name","Star Trek TNG"); }});
    // Returns Array(HashMap( ("name","Worf") , ("show","Star Trek TNG") ),HashMap( ("name","Data") , ("show","Star Trek TNG") ))

# License 
rethinkjava - Java Drivers for RethinkDB

    Copyright (C) 2013  D.K.

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU Affero General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU Affero General Public License for more details.

    You should have received a copy of the GNU Affero General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.
