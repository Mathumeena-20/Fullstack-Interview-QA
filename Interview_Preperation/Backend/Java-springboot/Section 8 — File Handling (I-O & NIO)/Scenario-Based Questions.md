
# ⭐ 1. How do you read and process large log files efficiently?

### **Best choices:**

✔ **BufferedReader** (line by line)
✔ **Files.lines()** (streamed)
✔ **FileChannel + ByteBuffer** (most efficient)

### Example using `Files.lines()` — memory efficient:

```java
try (Stream<String> stream = Files.lines(Paths.get("app.log"))) {
    stream.forEach(System.out::println);
}
```

### Example using `BufferedReader`:

```java
try (BufferedReader br = Files.newBufferedReader(Paths.get("app.log"))) {
    String line;
    while ((line = br.readLine()) != null) {
        // Process each line
    }
}
```

### Why this is efficient?

✔ Does NOT load whole file in memory
✔ Streams read chunk by chunk
✔ Works well for multi-GB logs

---

# ⭐ 2. How would you design a file upload/download feature using NIO?

### File Upload (Server-side):

```java
public void uploadFile(InputStream input, Path target) throws Exception {
    try (ReadableByteChannel from = Channels.newChannel(input);
         FileChannel to = FileChannel.open(target, StandardOpenOption.CREATE, StandardOpenOption.WRITE)) {

        to.transferFrom(from, 0, Long.MAX_VALUE); // Zero-copy
    }
}
```

### File Download:

```java
public void downloadFile(Path source, OutputStream output) throws Exception {
    try (FileChannel from = FileChannel.open(source);
         WritableByteChannel to = Channels.newChannel(output)) {

        from.transferTo(0, from.size(), to);
    }
}
```

✔ Uses **zero-copy**
✔ High performance
✔ Ideal for REST APIs and microservices

---

# ⭐ 3. How do you serialize objects safely in a microservices environment?

Serialization in microservices must be:

✔ Safe
✔ Versioned
✔ Backward-compatible
✔ Secure

### Best practices:

### ✔ 1. Avoid Java native serialization

⚠️ It is insecure and slow
Alternative formats:

* JSON
* Protobuf
* Avro
* MessagePack

### ✔ 2. Use DTO classes (never expose domain classes)

### ✔ 3. Define version fields

```json
{
 "version": 2,
 "name": "John"
}
```

### ✔ 4. Validate before deserializing

Never trust external input.

### ✔ 5. Disable dangerous classes using ObjectInputFilter (Java 9+):

```java
ObjectInputFilter filter = ObjectInputFilter.Config.createFilter("com.myapp.Student;!*");
in.setObjectInputFilter(filter);
```

---

# ⭐ 4. What are the performance differences between IO and NIO?

| Feature               | IO (Stream)  | NIO (Channel + Buffer) |
| --------------------- | ------------ | ---------------------- |
| API Type              | Blocking     | Non-blocking           |
| Data Handling         | Byte-by-byte | Blocks (buffers)       |
| Thread per connection | Yes          | No                     |
| Scalability           | Low          | High                   |
| Zero-copy             | No           | Yes                    |
| Performance           | Slower       | Faster                 |

### When to use NIO?

✔ High concurrency
✔ File transfer
✔ Socket servers
✔ Large files

---

# ⭐ 5. How do you prevent serialization vulnerabilities?

### ✔ Use `ObjectInputFilter` (Java 9+)

```java
ObjectInputFilter filter = ObjectInputFilter.Config.createFilter("maxbytes=1024;!*");
in.setObjectInputFilter(filter);
```

### ✔ Avoid native Java serialization

Use JSON/Protobuf instead.

### ✔ Use `transient` for sensitive fields

```java
private transient String password;
```

### ✔ Never deserialize untrusted data

### ✔ Validate class types before deserialization

---

# ⭐ 6. Read a large CSV file and count distinct values efficiently

```java
try (Stream<String> lines = Files.lines(Paths.get("data.csv"))) {

    long distinctCount = lines
        .map(line -> line.split(",")[2]) // get 3rd column
        .distinct()
        .count();

    System.out.println("Distinct values = " + distinctCount);
}
```

✔ Uses streaming
✔ Handles multi-GB CSV
✔ Avoids loading full file

---

# ⭐ 7. Serialize a Student object and deserialize it back

### Class:

```java
class Student implements Serializable {
    private static final long serialVersionUID = 1L;
    String name;
    int age;

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

### Serialize:

```java
Student s = new Student("John", 20);

ObjectOutputStream out = new ObjectOutputStream(new FileOutputStream("s.ser"));
out.writeObject(s);
out.close();
```

### Deserialize:

```java
ObjectInputStream in = new ObjectInputStream(new FileInputStream("s.ser"));
Student s2 = (Student) in.readObject();
in.close();
```

---

# ⭐ 8. Use NIO to copy a file faster than old I/O streams

```java
Path src = Paths.get("bigfile.dat");
Path dest = Paths.get("copy.dat");

try (FileChannel from = FileChannel.open(src);
     FileChannel to = FileChannel.open(dest, StandardOpenOption.CREATE, StandardOpenOption.WRITE)) {

    from.transferTo(0, from.size(), to);  // zero-copy
}
```

✔ Much faster than stream copy
✔ Minimal CPU overhead

---

# ⭐ 9. Monitor a folder for new files (WatchService)

```java
WatchService watcher = FileSystems.getDefault().newWatchService();

Path dir = Paths.get("inbox");
dir.register(watcher, StandardWatchEventKinds.ENTRY_CREATE);

while (true) {
    WatchKey key = watcher.take();
    for (WatchEvent<?> event : key.pollEvents()) {
        System.out.println("New file: " + event.context());
    }
    key.reset();
}
```

✔ Used for log monitoring
✔ File arrival processing
✔ Directory-based workflows

---

# ⭐ 10. List all files larger than 100 MB

```java
try (Stream<Path> paths = Files.walk(Paths.get("data"))) {

    paths.filter(Files::isRegularFile)
         .filter(p -> {
             try {
                 return Files.size(p) > 100 * 1024 * 1024;
             } catch (IOException e) {
                 return false;
             }
         })
         .forEach(System.out::println);
}
```

✔ Works recursively
✔ Efficient for large file systems

---

# ⭐ Final Interview Summary

| Topic                         | Key Points                                       |
| ----------------------------- | ------------------------------------------------ |
| Read large logs               | Files.lines(), BufferedReader, FileChannel       |
| File upload/download          | Use Channels + zero-copy                         |
| Safe serialization            | Validate, filter, avoid native serialization     |
| IO vs NIO performance         | NIO faster & scalable                            |
| Prevent vulnerabilities       | ObjectInputFilter, transient, no untrusted input |
| Count distinct CSV values     | Streaming + distinct()                           |
| Student serialize/deserialize | Serializable + writeObject/readObject            |
| Fast copy                     | FileChannel.transferTo                           |
| Monitor folder                | WatchService                                     |
| Files > 100 MB                | Files.walk + Files.size                          |

---

✔ End-to-end “file ingestion service” architecture
✔ Coding problem: process huge logs in parallel using NIO + parallel streams
