# common-errors
A list of common errors I get, along with their fixes

# No mapping found for WEB-INF
This nasty error can occur while working with spring boot. You have some JSP files within your WEB_INF that simply can't be found, even when you have given the correct path 
inside your properties file. Let's move on to the fix

From this
```
        <dependency>
            <groupId>org.apache.tomcat.embed</groupId>
            <artifactId>tomcat-embed-jasper</artifactId>
            <version>9.0.44</version>
        </dependency>
```
To this
```
        <dependency>
            <groupId>org.apache.tomcat.embed</groupId>
            <artifactId>tomcat-embed-jasper</artifactId>
        </dependency>
```

Do not touch this
```
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>jstl</artifactId>
            <version>1.2</version>
        </dependency>
```

Remove these 2
```
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>servlet-api</artifactId>
            <version>2.5</version>
            <scope>provided</scope>
        </dependency>
        
        <dependency>
            <groupId>javax.servlet.jsp</groupId>
            <artifactId>jsp-api</artifactId>
            <version>2.1</version>
            <scope>provided</scope>
        </dependency>
```

Update 24/12/2021

Turns out perform a mvn install, invalidating the caches then restarting on intellij has solved the problem. Perhaps it has nothing to do with the dependencies
