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
