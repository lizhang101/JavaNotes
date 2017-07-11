> The java String is immutable i.e. it cannot be changed. Whenever we change any string, a new instance is created. For mutable string, you can use **StringBuffer** and **StringBuilder** classes

> Note: String objects are stored in a special memory area known as string constant pool.
> JVM will look up the string literal in the pool before creating a string object. So, it will not create a new object if this string has same literal as some string object created before.