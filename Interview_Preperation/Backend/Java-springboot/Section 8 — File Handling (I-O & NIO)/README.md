Here are **topic-wise Java interview questions** for a **2+ years experienced developer** on:

✅ Files API
✅ Directory Stream
✅ Buffers & Channels (NIO)
✅ Serialization

---

## 1. Files API (java.nio.file)

1. What is the Java NIO Files API?
2. Difference between `Files` and `File` class.
3. How do you read a file using `Files.readAllLines()`?
4. Difference between `Paths.get()` and `File`?
5. How do you write data to a file using `Files` class?
6. What is `Path` interface?
7. How do you check if a file exists using NIO?
8. How to copy, move and delete files using `Files` API?
9. How do you get file attributes using Files?
10. Explain `StandardOpenOption` with examples.
11. Difference between blocking IO and non-blocking IO.
12. How do you create temporary files and directories?
13. What is atomic file operation?
14. How do you read large files efficiently using `Files`?
15. Real-time use case where you preferred NIO Files over traditional IO.

---

## 2. Directory Stream

1. What is `DirectoryStream` in Java?
2. Difference between `DirectoryStream` and `File.listFiles()`?
3. How is DirectoryStream more memory efficient?
4. What is `DirectoryStream.Filter`?
5. How do you filter files using DirectoryStream?
6. Can DirectoryStream handle very large directories?
7. What is the use of `Files.newDirectoryStream()`?
8. Difference between `DirectoryStream` and `Stream<Path>`?
9. How does lazy loading work in DirectoryStream?
10. What happens if the directory content changes during iteration?
11. How do you manage exceptions while using DirectoryStream?
12. Is DirectoryStream thread-safe?
13. How do you close DirectoryStream resources?
14. How to scan directories recursively?
15. Where did you use DirectoryStream in a real project?

---

## 3. Buffers & Channels (Java NIO)

1. What are Buffers and Channels in Java NIO?
2. Difference between InputStream/OutputStream and Channels?
3. Difference between blocking IO and non-blocking IO.
4. Types of buffers in Java (ByteBuffer, CharBuffer, etc.)?
5. Difference between HeapBuffer and DirectBuffer.
6. What are the main properties of Buffer? (`capacity`, `limit`, `position`, `mark`)
7. What is a Channel?
8. Types of channels in Java NIO.
9. Difference between `ReadableByteChannel` and `WritableByteChannel`.
10. What is Selector in Java NIO?
11. How does Java NIO support multiplexing?
12. What is zero-copy in Java NIO?
13. Explain FileChannel vs SocketChannel.
14. How does non-blocking IO improve performance in servers?
15. Real-world use of NIO in high-performance applications.

---

## 4. Serialization

1. What is serialization in Java?
2. Difference between serialization and deserialization.
3. Why is serialization needed?
4. What is `Serializable` interface?
5. Difference between Serializable and Externalizable.
6. What is `serialVersionUID`?
7. What happens if `serialVersionUID` is not defined?
8. Role of `transient` keyword in serialization.
9. Can static variables be serialized?
10. How to customize serialization using `writeObject()` and `readObject()`?
11. What is deep vs shallow copy in serialization?
12. What is object graph?
13. How do you prevent sensitive data from being serialized?
14. What are common serialization issues?
15. Real-world example where you used serialization (ex: caching, session replication).

---

## 🔥 Scenario-Based Questions

1. How do you read and process large log files efficiently?
2. How would you design a file upload/download feature using NIO?
3. How do you serialize objects safely in a microservices environment?
4. What are the performance differences between IO and NIO?
5. How do you prevent serialization vulnerabilities?
6. Read a large CSV file and count distinct values efficiently.
7. Serialize a Student object and deserialize it back.
8. Use NIO to copy a file faster than I/O streams.
9. Monitor a folder for new files (WatchService).
10. List all files larger than 100 MB.
---

