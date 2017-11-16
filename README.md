# maven-repo
Love to my own maven-repo release =D

Tutorial:
http://coffeecoders.de/2011/09/using-github-as-a-personal-maven-repository/

## How to use the repository

### pom.xml

    <repositories>
      <repository>
          <id>khaing211-public-releases</id>
          <url>https://raw.github.com/khaing211/maven-repo/master/releases</url>
      </repository>
    </repositories>

### build.gradle

    repositories {
      maven {
          url "https://raw.github.com/khaing211/maven-repo/master/releases"
      }
    }
  
## How to deploy artifact

### pom.xml

    <distributionManagement>
        <repository>
            <id>khaing211-public-releases</id>
            <url>https://raw.github.com/khaing211/maven-repo/master/releases</url>
        </repository>
    </distributionManagement>
    
Clone the git repository locally :

    git clone git@github.com:khaing211/maven-repo.git

Then deploy the files in your local repo

    mvn -DaltDeploymentRepository=snapshot-repo::default::file:PATH_TO/maven-repo/releases/ clean deploy

And commit and push your changes to github:

    git commit -m "UPDATE"
    git push origin master

### build.gradle

    uploadArchives {
        repositories {
            mavenDeployer {
                repository(url: "file://${localMavenRepo}")
            }
        }
    }

Then deploy the files in your local repo

    gradle -PlocalMavenRepo=/path/to/maven-repo uploadArchives
    
POM generation, customization, etc.. please read
http://gradle.org/docs/current/userguide/maven_plugin.html#uploading_to_maven_repositories

### Using maven-publish

    gradle -PlocalMavenRepo=/path/to/maven-repo/releases publishToMavenLocal publish

### How to deploy existing/3rdparty jar without pom.xml

    mvn install:install-file -Dfile=/path/to/jar -DgroupId=alice.tuprolog -DartifactId=tuprolog -Dversion=3.0.1 -DlocalRepositoryPath=/path/to/local/repo -Dpackaging=jar -DgeneratePom=true -DcreateChecksum=true
        
