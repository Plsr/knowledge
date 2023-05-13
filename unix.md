# Unix

## mkdir

### Create intermediate directories

Use the `-p` option:

```bash
$ mkdir -p /new/also-new/new-as-well
```

Will create the `new`, `also-new` as well as the `new-as-well` dirs.

From the manpages:

> Create intermediate directories as required.  If this option is not specified, the full path prefix of each operand must already exist.  On the other hand, with this option specified, no error will be reported if a directory given as an operand already exists.  Intermediate directories are created with permission bits of “rwxrwxrwx” (0777) as modified by the current umask, plus write and search permission for the owner.
