# @PackagePrivate

PackagePrivate annotation to identify intended java default access modifier.
This indicates that the default access is by design and not an error.
Currently the annotation can be applied to fields, methods and constructors (I may add more).

The jar includes a processor to give a compile time error if a non-default (public, protected, private) is used with the annotation.

## Usage
Add the following to your build.gradle:
```groovy
...
repositories { 
  maven { 
    url "http://dl.bintray.com/jaimiew/whijai" 
  }
}
dependencies {
	compile 'com.github.jaimiew:package-private:0.0.1'

}
...
```
Then you can annotate fields, methods and constructors, for example fields:
```java
public class Foo {
  private a;            // private instance variable
  @PackagePrivate b;    // default access instance variable
  protected c;          // protected access instance variable
  public d;             // public access instance variable
}
```
And similarly for methods and constructors.

To turn on the processor in eclipse, 
* go to Project->Properties->Java Compiler->Annotation Processing
* Enable annotation processing
* go to Factory Path
* add the package-private.jar as an external jar
<br />
[source](https://deors.wordpress.com/2011/10/08/annotation-processors/)
