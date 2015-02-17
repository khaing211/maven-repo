# maven-repo
Love to my own maven-repo release =D

Tutorial:
http://coffeecoders.de/2011/09/using-github-as-a-personal-maven-repository/

## How to use it

In pom.xml

    <repositories>
      <repository>
          <id>khaing211-public-releases</id>
          <url>https://raw.github.com/khaing211/maven-repo/master/releases</url>
      </repository>
    </repositories>

In build.gradle

    repositories {
      maven {
          url "https://raw.github.com/khaing211/maven-repo/master/releases"
      }
    }
  
