# Sed Command

`sed` stands for **stream editor**.

Basic usage:

```bash
sed 's/oldtext/newtext/' file.txt
```

This replaces the first occurrence of `oldtext` with `newtext` in each line and prints the result to the console.

Replace all occurrences:

```bash
sed 's/oldtext/newtext/g' file.txt
```

## Save changes to the file

### Linux

```bash
sed -i 's/oldtext/newtext/g' file.txt
```

### macOS

```bash
sed -i '' 's/oldtext/newtext/g' file.txt
```

macOS requires an empty string after `-i`.

## Print Specific Line

Print line 5:

```bash
sed -n '5p' file.txt
```

Print lines 5 to 10:

```bash
sed -n '5,10p' file.txt
```

`-n` prevents sed from printing every line automatically.

---

## Delete Lines

Delete line 3:

```bash
sed '3d' file.txt
```

Delete lines 3 to 5:

```bash
sed '3,5d' file.txt
```

Delete empty lines:

```bash
sed '/^$/d' file.txt
```
