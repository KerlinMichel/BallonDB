# BallonDB :balloon:

BallonDB is an object relational database. It is build on Java and it follows the ideas of object orient programming.

How to add a client-side Database for devs


```java
package bdb.demo;
import BallonDB.DataObject;
/* BallonDB only accepts DataObjects to ensure
   that the class is serializable and have other
   necessary things such as a key.
*/
public class CustomObject extends DataObject {
	String name;
    double id;
    public CustomObject(String name, double id) {
    	this.name = name;
        this.id = id;
    }
}
```

```java
CustomObject obj1 = new CustomObject("Some-name", 15.2D);
CustomObject obj2 = new CustomObject("Diff-name", 45D);

BallonDB bdb = new BallonDB(new File("/Test")); 
bdb.insert(obj1);
bdb.insert(obj2);
bdb.forceSave();

bdb.select("CustomObject where name = Some-name");
bdb.delete("CustomObjecy where id = 45");
```
The physical file will be save in /Test followed by the class path, in this case /bdb/demo, and the file name with by an auto-generated UUID. So it will under /Test/bdb/demo/{some UUID}.ser
