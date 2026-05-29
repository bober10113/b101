# Patch Copy Note

The local patch file is the source of truth:

```text
C:\Users\nufan\Documents\Frigate go2rtc\b101-nest-sessionfix-clean.lf.patch
```

The GitHub branch currently contains a manually uploaded copy at:

```text
go2rtc-nest-sessionfix/b101-nest-sessionfix-clean.lf.patch
```

During sanity review, one manual copy/paste issue was found in the final hunk of the GitHub copy:

```diff
-	}
```

That line should be:

```diff
-}
```

The local `.lf.patch` file already has the correct version and was previously validated as ASCII-only, LF-only, and matching 13 hunks against AlexxIT/go2rtc commit:

```text
dc1685e9cf7a8c349181f20a1b4a44825ed394c5
```

Use the local patch file for applying/building until the GitHub patch copy is regenerated directly from the file rather than manually pasted.
