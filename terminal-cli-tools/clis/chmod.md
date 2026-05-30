# Chmod



* `0`: No permission
* `1`: Execute permission
* `2`: Write permission
* `3`: Write and execute permissions
* `4`: Read permission
* `5`: Read and execute permissions
* `6`: Read and write permissions
* `7`: Read, write, and execute permissions



The core difference between `chmod 600` and `chmod 700` is that **`600` only allows the owner to read and write** a file, while **`700` allows the owner to read, write, and execute**.

```
 A numeric mode is from one to four octal digits (0-7), derived by
       adding up the bits with values 4, 2, and 1.  Omitted digits are
       assumed to be leading zeros.  The first digit selects the set user
       ID (4) and set group ID (2) and restricted deletion or sticky (1)
       attributes.  The second digit selects permissions for the user who
       owns the file: read (4), write (2), and execute (1); the third
       selects permissions for other users in the file's group, with the
       same values; and the fourth for other users not in the file's
       group, with the same values.
```

