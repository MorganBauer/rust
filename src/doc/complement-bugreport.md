% How to submit a Rust bug report

# I think I found a bug in the compiler!

If you see this message: `error: internal compiler error: unexpected panic`,
then you have definitely found a bug in the compiler. It's also possible that
your code is not well-typed, but if you saw this message, it's still a bug in
error reporting.

If you see a message about an LLVM assertion failure, then you have also
definitely found a bug in the compiler. In both of these cases, it's not your
fault and you should report a bug!

If you see a compiler error message that you think is meant for users to see,
but it confuses you, *that's a bug too*. If it wasn't clear to you, then it's
an error message we want to improve, so please report it so that we can try
to make it better.

# How do I know the bug I found isn't a bug that already exists in the issue tracker?

If you don't have enough time for a search, then don't worry about that. Just submit
the bug. If it's a duplicate, somebody will notice that and close it during triage.

If you have the time for it, it would be useful to type the text of the error
message you got [into the issue tracker search box](https://github.com/rust-lang/rust/issues)
to see if there's an existing bug that resembles your problem. If there is,
and it's an open bug, you can comment on that issue and say you are also affected.
This will encourage the devs to fix it. But again, don't let this stop you from
submitting a bug. We'd rather have to do the work of closing duplicates than
miss out on valid bug reports.

# What information should I include in a bug report?

It generally helps our diagnosis to include your specific OS (for example: Mac OS X 10.8.3,
Windows 7, Ubuntu 12.04) and your hardware architecture (for example: i686, x86_64).
It's also helpful to provide the exact version and host by copying the output of
re-running the erroneous rustc command with the `--version --verbose` flags, which will
produce something like this:

```text
rustc 0.12.0 (ba4081a5a 2014-10-07 13:44:41 -0700)
binary: rustc
commit-hash: ba4081a5a8573875fed17545846f6f6902c8ba8d
commit-date: 2014-10-07 13:44:41 -0700
host: i686-apple-darwin
release: 0.12.0
```

Finally, if you can also provide a backtrace, that'd be great. You can get a
backtrace by setting the `RUST_BACKTRACE` environment variable to `1`, like
this: 

```bash
$ RUST_BACKTRACE=1 rustc ...
```

# I submitted a bug, but nobody has commented on it!

This is sad, but does happen sometimes, since we're short-staffed. If you submit a
bug and you haven't received a comment on it within 3 business days, it's entirely
reasonable to ask about the status of the bug in #rust on irc.mozilla.org.
