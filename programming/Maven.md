
=== settings.xml ===
settings
	localRepository
	interactiveMode
	offlnie
	pluginGroups
	servers
	misrors
	proxies
	profiles
	avtiveProfiles
	
=== pom.xml ===
project
	parent
	module
	groupId
	artifactId
	version
	packaging
	name
	description
	organization
	licneses
	mailingList
	developers
	contributors
	issueManagment
	ciMamagement
	scm
	prerequisites
	build
		sourceDirectory
		scriptSourceDirectory
		outputDirectory
		testSourceDirectory
		testOutputDirectory
		resources
		testResources
		finalName
		directory
		filters
		extensions
		pluginManagement
		plugins
		profile
	distributionManagement
		repositiory
		sanpshotRepository
		site
		repository
		pluginRepostory
		depnedency
	dependencyManagement
	properties
	reporting
		plugins
		
Initialize a general project:

mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false

mvn archetype:generate -DgroupId=cn.luxh.app -DartifactId=my-web-app -DarchetypeArtifactId=maven-archetype-webapp -DinteractivMode=false

$ mvn dependency:copy-dependencies -DoutputDirectory=OUTPUT_DIR

<build>
  <plugins>
	<plugin>
	  <artifactId>maven-assembly-plugin</artifactId>
	  <configuration>
		<descriptorRefs>
		  <descriptorRef>jar-with-dependencies</descriptorRef>
		</descriptorRefs>
		<archive>
		  <manifest>
			<mainClass>fully.qualified.MainClass</mainClass>
		  </manifest>
		</archive>
	  </configuration>
	</plugin>
  </plugins>
</build>


<build>
  <plugins>
	<plugin>
	  <artifactId>maven-assembly-plugin</artifactId>
	  <configuration>
		<descriptorRefs>
		  <descriptorRef>jar-with-dependencies</descriptorRef>
		</descriptorRefs>
		<archive>
		  <manifest>
			<mainClass>fully.qualified.MainClass</mainClass>
		  </manifest>
		</archive>
	  </configuration>
	  <executions>
		<execution>
		  <phase>package</phase>
		  <goals>
			<goal>single</goal>
		  </goals>
		</execution>
	  </executions>
	</plugin>
  </plugins>
</build>


mvn clean compile
mvn clean test
mvn clean package
mvn clean install

mvn dependency:list
mvn dependency:tree
mvn dependency:analyze

			<plugin>
				<groupId>org.apache.tomcat.maven</groupId>
				<artifactId>tomcat7-maven-plugin</artifactId>
				<version>2.0</version>
				<configuration>
					<path>/</path>
					<port>8080</port>
				</configuration>
			</plugin>


tomcat7:run

