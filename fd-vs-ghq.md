# fd vs ghq

## Environment

### Version

|                       Name                        |       Version       |
| ------------------------------------------------- | ------------------- |
| [hyperfine](https://github.com/sharkdp/hyperfine) | 1.9.0               |
| [fd](https://github.com/sharkdp/fd)               | 7.4.0               |
| [ghq](https://github.com/motemen/ghq)             | 1.0.1 (rev:91944fb) |

### Misc

```
$ ghq list | wc -l
    943
```

## Benchmarks

```
$ hyperfine 'fd . $(ghq root) --type d --max-depth 3' 'ghq list -p'
```

|                  Command                  |   Mean [ms]    | Min [ms] | Max [ms] |  Relative   |
| :---------------------------------------- | -------------: | -------: | -------: | ----------: |
| `fd . $(ghq root) --type d --max-depth 3` | **83.9 ± 8.0** |     75.8 |    108.5 |        1.00 |
| `ghq list -p`                             |   581.8 ± 27.2 |    552.8 |    636.4 | 6.93 ± 0.74 |

```
$ hyperfine 'fd . $(ghq root) --type d --max-depth 3' 'ghq list -p --vcs=git'
```

|                  Command                  |   Mean [ms]    | Min [ms] | Max [ms] |  Relative   |
| :---------------------------------------- | -------------: | -------: | -------: | ----------: |
| `fd . $(ghq root) --type d --max-depth 3` | **84.9 ± 6.6** |     76.2 |    105.4 |        1.00 |
| `ghq list -p --vcs=git`                   |   346.0 ± 13.5 |    332.1 |    377.2 | 4.08 ± 0.36 |
