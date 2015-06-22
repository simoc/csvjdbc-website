##Building From Source

To checkout and build the latest source code from the
[CsvJdbc git repository](http://sourceforge.net/p/csvjdbc/code/ci/master/tree/),
use the following commands ([git](http://git-scm.com/) and
[Maven](http://maven.apache.org/) must first be installed).

    git clone git://git.code.sf.net/p/csvjdbc/code csvjdbc
    cd csvjdbc
    mvn install
    cd target
    dir csvjdbc*.jar

##Maven Project Usage

To include CsvJdbc in a [Maven](http://maven.apache.org/) project,
add the following lines to the `pom.xml` file.

    <project>
     ...
      <repositories>
        <repository>
          <id>SourceForge</id>
          <url>http://csvjdbc.sourceforge.net/maven2</url>
        </repository>
      </repositories>
    
      <dependencies>
        <dependency>
          <groupId>net.sourceforge.csvjdbc</groupId>
          <artifactId>csvjdbc</artifactId>
          <version>1.0.25</version>
        </dependency>
      </dependencies>

