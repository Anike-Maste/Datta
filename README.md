# Datta
<project xmlns="http://maven.apache.org/POM/4.0.0"                < these lines are to connect central
	 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"        < repo where we have plugins dependencies to be downloaded >
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
	<modelVersion>4.0.0</modelVersion>   < the model version will help to give unique version name>  
	<groupId>com.mkyong</groupId>  < its reverse of your website , like reverse of google.com is com.google>
	<artifactId>CounterWebApp</artifactId> < this is the name of your application>
	<packaging>jar</packaging> < its for the packaging , it can be war,ear,jar>
	<version>1.0-SNAPSHOT</version> < incremental version 1.0 or 1.1 or 1.1.1>
	<name>CounterWebApp Maven Webapp</name>  < name of the application>
	<url>http://maven.apache.org</url> <url of the application>
	<properties>    <properties help to define our version of dependencies and change them accordingly>
		<jdk.version>1.7</jdk.version>
		<spring.version>4.1.1.RELEASE</spring.version>
		<jstl.version>1.2</jstl.version>
		<junit.version>4.11</junit.version>
		<logback.version>1.0.13</logback.version>
		<jcl-over-slf4j.version>1.7.5</jcl-over-slf4j.version>
	</properties>	
	<dependencies>	< dependencies are the libraries which help us to run the program , imporper dependencies will result in compilation error>
	<!-- Unit Test -->
		<dependency>
			<groupId>junit</groupId>  <will be the name of the dependency>
			<artifactId>junit</artifactId>  < be the artifcat id . like jar file name junit.jar>
			<version>${junit.version}</version> < here junit version will be pointed to the above properties where we have junit verion 4.11>
		</dependency>
		<!-- Spring Core -->
		<dependency>
			<groupId>org.springframework</groupId> 
			<artifactId>spring-core</artifactId>
			<version>${spring.version}</version>
			<exclusions>
				<exclusion> <exclude what you dont require>
					<groupId>commons-logging</groupId>
					<artifactId>commons-logging</artifactId>
				</exclusion>
			</exclusions>
		</dependency>
		<dependency>
			<groupId>org.slf4j</groupId>
			<artifactId>jcl-over-slf4j</artifactId>
			<version>${jcl-over-slf4j.version}</version>
		</dependency>

		<dependency>
			<groupId>ch.qos.logback</groupId>
			<artifactId>logback-classic</artifactId>
			<version>${logback.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-web</artifactId>
			<version>${spring.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-webmvc</artifactId>
			<version>${spring.version}</version>
		</dependency>
		<!-- jstl -->
		<dependency>
			<groupId>jstl</groupId>
			<artifactId>jstl</artifactId>
			<version>${jstl.version}</version>
		</dependency>
	</dependencies>
	<build>
		<finalName>CounterWebApp</finalName>
		<plugins>
		    <!-- Eclipse project -->
			<plugin>  <define the plugins , different plugins for different goals like clean , install ,deploy>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-eclipse-plugin</artifactId>
				<version>2.9</version>
				<configuration>
				    <!-- Always download and attach dependencies source code -->
					<downloadSources>true</downloadSources>
					<downloadJavadocs>false</downloadJavadocs>
					<!-- mvn eclipse:eclipse -Dwtpversion=2.0 -->
					<wtpversion>2.0</wtpversion>
				</configuration>
			</plugin>	
			<!-- Set JDK Compiler Level -->
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-compiler-plugin</artifactId> < this is compiler plugin>
				<version>2.3.2</version>
				<configuration>
					<source>${jdk.version}</source>
					<target>${jdk.version}</target>
				</configuration>
			</plugin>
			<!-- For Tomcat -->
			<plugin>
				<groupId>org.apache.tomcat.maven</groupId>
				<artifactId>tomcat7-maven-plugin</artifactId> < this is tomcat plugin>
				<version>2.2</version>
				<configuration>
					<path>/CounterWebApp</path>
				</configuration>
			</plugin>
		</plugins>
	</build>
