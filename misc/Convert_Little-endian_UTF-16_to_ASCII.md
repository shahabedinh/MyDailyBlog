##  Convert Little-endian UTF-16 to ascii

I have to check logs (from others), and had an issue to grep word, or use Atom to Find the word.

I checked the file by `file` command and found it is Little-endian UTF-16 Unicode text file format.

```bash
| ==> file some-logs.log
some-logs.log: Little-endian UTF-16 Unicode text, with very long lines, with CRLF line terminators
```

I converted to ascii by

```bash
iconv -f utf-16 -t utf-8  some-logs.log > some-logs-new.log
```