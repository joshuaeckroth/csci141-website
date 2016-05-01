---
title: Files
layout: default
---

## File input

Use `FileInputStream` and `BufferedInputStream`

```
FileInputStream is = new FileInputStream("filename.txt");
```

Possible exceptions:

- `FileNotFoundException`
- `SecurityException` -- if you're not allowed to read the file
- `IOException` -- some other problem reading the file

### `Scanner` for file input

```
Scanner fin = new Scanner(is); // FileInputStream 'is' from above
int n = fin.nextInt(); // usual Scanner methods
```

## File output

Use a `PrintWriter` for text files.

```
PrintWriter writer = new PrintWriter("filename.txt");
writer.println("Some text...");
writer.print(55); // print a number
writer.println(); // move to next line
writer.close();
```

Possible exceptions:

- `FileNotFoundException`
- `SecurityException` -- if you're not allowed to read the file
