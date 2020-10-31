# Developer API
[Back to uhcplus](/wiki/plugins/uhcplus/index.md)

You can add UhcPlus as a dependency, and build on top of it!

You have to replace 'Tag' with whatever version of UhcPlus you want to use. E.g `0.5-BETA`

### Gradle
```
allprojects {
	repositories {
		maven { url 'https://jitpack.io' }
	}
}
```
```
dependencies {
	implementation 'nl.thedutchmc:uhcplus:Tag'
}
```
### Maven
```
<repositories>
	<repository>
	    <id>jitpack.io</id>
            <url>https://jitpack.io</url>
        </repository>
</repositories>
```
```
<dependency>
	<groupId>nl.thedutchmc</groupId>
	<artifactId>uhcplus</artifactId>
        <version>Tag</version>
</dependency>
```
### SBT
```
resolvers += "jitpack" at "https://jitpack.io"
```
```
libraryDependencies += "nl.thedutchmc" % "uhcplus" % "Tag"	
```
### Leiningen
```
:repositories [["jitpack" "https://jitpack.io"]]
```
```
:dependencies [[nl.thedutchmc/uhcplus "Tag"]]	
```