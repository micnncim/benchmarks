# fd vs ghq

[fd](https://github.com/sharkdp/fd) vs [ghq](https://github.com/motemen/ghq)

## Environment

```
$ hyperfine --version
hyperfine 1.9.0
$ fd --version
fd 7.4.0
$ ghq --version
ghq version 1.0.1 (rev:91944fb)
```

## Benchmarks

```
$ hyperfine 'fd . $(ghq root) --type d --max-depth 3' 'ghq list -p'
Benchmark #1: fd . $(ghq root) --type d --max-depth 3
  Time (mean ± σ):      82.4 ms ±   9.0 ms    [User: 315.8 ms, System: 117.3 ms]
  Range (min … max):    74.1 ms … 117.6 ms    24 runs

Benchmark #2: ghq list -p
  Time (mean ± σ):     567.7 ms ±  16.7 ms    [User: 674.5 ms, System: 2901.8 ms]
  Range (min … max):   550.9 ms … 600.0 ms    10 runs

Summary
  'fd . $(ghq root) --type d --max-depth 3' ran
    6.89 ± 0.78 times faster than 'ghq list -p'
```

```
$ hyperfine 'fd . $(ghq root) --type d --max-depth 3' 'ghq list -p --vcs=git'
Benchmark #1: fd . $(ghq root) --type d --max-depth 3
  Time (mean ± σ):      83.6 ms ±   7.1 ms    [User: 319.3 ms, System: 118.7 ms]
  Range (min … max):    73.9 ms … 105.6 ms    32 runs

Benchmark #2: ghq list -p --vcs=git
  Time (mean ± σ):     349.7 ms ±  23.0 ms    [User: 508.8 ms, System: 1633.1 ms]
  Range (min … max):   320.5 ms … 396.3 ms    10 runs

Summary
  'fd . $(ghq root) --type d --max-depth 3' ran
    4.18 ± 0.45 times faster than 'ghq list -p --vcs=git'
```