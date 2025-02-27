1.18.1 - 2019-08-11
===================

### Fixes
- Fix installation of `rust` hooks with new `cargo`
    - #1112 issue by @zimbatm.
    - #1113 PR by @zimbatm.

1.18.0 - 2019-08-03
===================

### Features
- Use the current running executable if it matches the requested
  `language_version`
    - #1062 PR by @asottile.
- Print the stage when a hook is not found
    - #1078 issue by @madkinsz.
    - #1079 PR by @madkinsz.
- `pre-commit autoupdate` now supports non-`master` default branches
    - #1089 PR by @asottile.
- Add `pre-commit init-templatedir` which makes it easier to automatically
  enable `pre-commit` in cloned repositories.
    - #1084 issue by @ssbarnea.
    - #1090 PR by @asottile.
    - #1107 PR by @asottile.
- pre-commit's color can be controlled using
  `PRE_COMMIT_COLOR={auto,always,never}`
    - #1073 issue by @saper.
    - #1092 PR by @geieredgar.
    - #1098 PR by @geieredgar.
- pre-commit's color can now be disabled using `TERM=dumb`
    - #1073 issue by @saper.
    - #1103 PR by @asottile.
- pre-commit now supports `docker` based hooks on windows
    - #1072 by @cz-fish.
    - #1093 PR by @geieredgar.

### Fixes
- Fix shallow clone
    - #1077 PR by @asottile.
- Fix autoupdate version flip flop when using shallow cloning
    - #1076 issue by @mxr.
    - #1088 PR by @asottile.
- Fix autoupdate when the current revision is invalid
    - #1088 PR by @asottile.

### Misc.
- Replace development instructions with `tox --devenv ...`
    - #1032 issue by @yoavcaspi.
    - #1067 PR by @asottile.


1.17.0 - 2019-06-06
===================

### Features
- Produce better output on `^C`
    - #1030 PR by @asottile.
- Warn on unknown keys at the top level and repo level
    - #1028 PR by @yoavcaspi.
    - #1048 PR by @asottile.

### Fixes
- Fix handling of `^C` in wrapper script in python 3.x
    - #1027 PR by @asottile.
- Fix `rmtree` for non-writable directories
    - #1042 issue by @detailyang.
    - #1043 PR by @asottile.
- Pass `--color` option to `git diff` in `--show-diff-on-failure`
    - #1007 issue by @chadrik.
    - #1051 PR by @mandarvaze.

### Misc.
- Fix test when `pre-commit` is installed globally
    - #1032 issue by @yoavcaspi.
    - #1045 PR by @asottile.


1.16.1 - 2019-05-08
===================

### Fixes
- Don't `UnicodeDecodeError` on unexpected non-UTF8 output in python health
  check on windows.
    - #1021 issue by @nicoddemus.
    - #1022 PR by @asottile.

1.16.0 - 2019-05-04
===================

### Features
- Add support for `prepare-commit-msg` hook
    - #1004 PR by @marcjay.

### Fixes
- Fix repeated legacy `pre-commit install` on windows
    - #1010 issue by @AbhimanyuHK.
    - #1011 PR by @asottile.
- Whitespace fixup
    - #1014 PR by @mxr.
- Fix CI check for working pcre support
    - #1015 PR by @Myrheimb.

### Misc.
- Switch CI from travis / appveyor to azure pipelines
    - #1012 PR by @asottile.

1.15.2 - 2019-04-16
===================

### Fixes
- Fix cloning non-branch tag while in the fallback slow-clone strategy.
    - #997 issue by @jpinner.
    - #998 PR by @asottile.

1.15.1 - 2019-04-01
===================

### Fixes
- Fix command length calculation on posix when `SC_ARG_MAX` is not defined.
    - #691 issue by @ushuz.
    - #987 PR by @asottile.

1.15.0 - 2019-03-30
===================

### Features
- No longer require being in a `git` repo to run `pre-commit` `clean` / `gc` /
  `sample-config`.
    - #959 PR by @asottile.
- Improve command line length limit detection.
    - #691 issue by @antonbabenko.
    - #966 PR by @asottile.
- Use shallow cloning when possible.
    - #958 PR by @DanielChabrowski.
- Add `minimum_pre_commit_version` top level key to require a new-enough
  version of `pre-commit`.
    - #977 PR by @asottile.
- Add helpful CI-friendly message when running
  `pre-commit run --all-files --show-diff-on-failure`.
  - #982 PR by @bnorquist.

### Fixes
- Fix `try-repo` for staged untracked changes.
    - #973 PR by @DanielChabrowski.
- Fix rpm build by explicitly using `#!/usr/bin/env python3` in hook template.
    - #985 issue by @tim77.
    - #986 PR by @tim77.
- Guard against infinite recursion when executing legacy hook script.
    - #981 PR by @tristan0x.

### Misc
- Add test for `git.no_git_env()`
    - #972 PR by @javabrett.

1.14.4 - 2019-02-18
===================

### Fixes
- Don't filter `GIT_SSH_COMMAND` env variable from `git` commands
    - #947 issue by @firba1.
    - #948 PR by @firba1.
- Install npm packages as if they were installed from `git`
    - #943 issue by @ssbarnea.
    - #949 PR by @asottile.
- Don't filter `GIT_EXEC_PREFIX` env variable from `git` commands
    - #664 issue by @revolter.
    - #944 PR by @minrk.

1.14.3 - 2019-02-04
===================

### Fixes
- Improve performance of filename classification by 45% - 55%.
    - #921 PR by @asottile.
- Fix installing `go` hooks while `GOBIN` environment variable is set.
    - #924 PR by @ashanbrown.
- Fix crash while running `pre-commit migrate-config` / `pre-commit autoupdate`
  with an empty configuration file.
    - #929 issue by @ardakuyumcu.
    - #933 PR by @jessebona.
- Require a newer virtualenv to fix metadata-based setup.cfg installs.
    - #936 PR by @asottile.

1.14.2 - 2019-01-10
===================

### Fixes
- Make the hook shebang detection more timid (1.14.0 regression)
    - Homebrew/homebrew-core#35825.
    - #915 PR by @asottile.

1.14.1 - 2019-01-10
===================

### Fixes
- Fix python executable lookup on windows when using conda
    - #913 issue by @dawelter2.
    - #914 PR by @asottile.

1.14.0 - 2019-01-08
===================

### Features
- Add an `alias` configuration value to allow repeated hooks to be
  differentiated
    - #882 issue by @s0undt3ch.
    - #886 PR by @s0undt3ch.
- Add `identity` meta hook which just prints filenames
    - #865 issue by @asottile.
    - #898 PR by @asottile.
- Factor out `cached-property` and improve startup performance by ~10%
    - #899 PR by @asottile.
- Add a warning on unexpected keys in configuration
    - #899 PR by @asottile.
- Teach `pre-commit try-repo` to clone uncommitted changes on disk.
    - #589 issue by @sverhagen.
    - #703 issue by @asottile.
    - #904 PR by @asottile.
- Implement `pre-commit gc` which will clean up no-longer-referenced cache
  repos.
    - #283 issue by @jtwang.
    - #906 PR by @asottile.
- Add top level config `default_language_version` to streamline overriding the
  `language_version` configuration in many places
    - #647 issue by @asottile.
    - #908 PR by @asottile.
- Add top level config `default_stages` to streamline overriding the `stages`
  configuration in many places
    - #768 issue by @mattlqx.
    - #909 PR by @asottile.

### Fixes
- More intelligently pick hook shebang (`#!/usr/bin/env python3`)
    - #878 issue by @fristedt.
    - #893 PR by @asottile.
- Several fixes related to `--files` / `--config`:
    - `pre-commit run --files x` outside of a git dir no longer stacktraces
    - `pre-commit run --config ./relative` while in a sub directory of the git
      repo is now able to find the configuration
    - `pre-commit run --files ...` no longer runs a subprocess per file
      (performance)
    - #895 PR by @asottile.
- `pre-commit try-repo ./relative` while in a sub directory of the git repo is
  now able to clone properly
    - #903 PR by @asottile.
- Ensure `meta` repos cannot have a language other than `system`
    - #905 issue by @asottile.
    - #907 PR by @asottile.
- Fix committing with unstaged files that were `git add --intent-to-add` added
    - #881 issue by @henniss.
    - #912 PR by @asottile.

### Misc
- Use `--no-gpg-sign` when running tests
    - #894 PR by @s0undt3ch.


1.13.0 - 2018-12-20
===================

### Features
- Run hooks in parallel
    - individual hooks may opt out of parallel exection with `require_serial: true`
    - #510 issue by @chriskuehl.
    - #851 PR by @chriskuehl.

### Fixes
- Improve platform-specific `xargs` command length detection
    - #691 issue by @antonbabenko.
    - #839 PR by @georgeyk.
- Fix `pre-commit autoupdate` when updating to a latest tag missing a
  `.pre-commit-hooks.yaml`
    - #856 issue by @asottile.
    - #857 PR by @runz0rd.
- Upgrade the `pre-commit-hooks` version in `pre-commit sample-config`
    - #870 by @asottile.
- Improve balancing of multiprocessing by deterministic shuffling of args
    - #861 issue by @Dunedan.
    - #874 PR by @chriskuehl.
- `ruby` hooks work with latest `gem` by removing `--no-ri` / `--no-rdoc` and
  instead using `--no-document`.
    - #889 PR by @asottile.

### Misc
- Use `--no-gpg-sign` when running tests
    - #885 PR by @s0undt3ch.

### Updating
- If a hook requires serial execution, set `require_serial: true` to avoid the new
  parallel execution.
- `ruby` hooks now require `gem>=2.0.0`.  If your platform doesn't support this
  by default, select a newer version using
  [`language_version`](https://pre-commit.com/#overriding-language-version).


1.12.0 - 2018-10-23
===================

### Fixes
- Install multi-hook repositories only once (performance)
    - issue by @chriskuehl.
    - #852 PR by @asottile.
- Improve performance by factoring out pkg_resources (performance)
    - #840 issue by @RonnyPfannschmidt.
    - #846 PR by @asottile.

1.11.2 - 2018-10-10
===================

### Fixes
- `check-useless-exclude` now considers `types`
    - #704 issue by @asottile.
    - #837 PR by @georgeyk.
- `pre-push` hook was not identifying all commits on push to new branch
    - #843 issue by @prem-nuro.
    - #844 PR by @asottile.

1.11.1 - 2018-09-22
===================

### Fixes
- Fix `.git` dir detection in `git<2.5` (regression introduced in
  [1.10.5](#1105))
    - #831 issue by @mmacpherson.
    - #832 PR by @asottile.

1.11.0 - 2018-09-02
===================

### Features
- Add new `fail` language which always fails
    - light-weight way to forbid files by name.
    - #812 #821 PRs by @asottile.

### Fixes
- Fix `ResourceWarning`s for unclosed files
    - #811 PR by @BoboTiG.
- Don't write ANSI colors on windows when color enabling fails
    - #819 PR by @jeffreyrack.

1.10.5 - 2018-08-06
===================

### Fixes
- Work around `PATH` issue with `brew` `python` on `macos`
    - Homebrew/homebrew-core#30445 issue by @asottile.
    - #805 PR by @asottile.
- Support `pre-commit install` inside a worktree
    - #808 issue by @s0undt3ch.
    - #809 PR by @asottile.

1.10.4 - 2018-07-22
===================

### Fixes
- Replace `yaml.load` with safe alternative
    - `yaml.load` can lead to arbitrary code execution, though not where it
      was used
    - issue by @tonybaloney.
    - #779 PR by @asottile.
- Improve not found error with script paths (`./exe`)
    - #782 issue by @ssbarnea.
    - #785 PR by @asottile.
- Fix minor buffering issue during `--show-diff-on-failure`
    - #796 PR by @asottile.
- Default `language_version: python3` for `python_venv` when running in python2
    - #794 issue by @ssbarnea.
    - #797 PR by @asottile.
- `pre-commit run X` only run `X` and not hooks with `stages: [...]`
    - #772 issue by @asottile.
    - #803 PR by @mblayman.

### Misc
- Improve travis-ci build times by caching rust / swift artifacts
    - #781 PR by @expobrain.
- Test against python3.7
    - #789 PR by @expobrain.

1.10.3 - 2018-07-02
===================

### Fixes
- Fix `pre-push` during a force push without a fetch
    - #777 issue by @domenkozar.
    - #778 PR by @asottile.

1.10.2 - 2018-06-11
===================

### Fixes
- pre-commit now invokes hooks with a consistent ordering of filenames
    - issue by @mxr.
    - #767 PR by @asottile.

1.10.1 - 2018-05-28
===================

### Fixes
- `python_venv` language would leak dependencies when pre-commit was installed
  in a `-mvirtualenv` virtualenv
    - #755 #756 issue and PR by @asottile.

1.10.0 - 2018-05-26
===================

### Features
- Add support for hooks written in `rust`
    - #751 PR by @chriskuehl.

1.9.0 - 2018-05-21
==================

### Features
- Add new `python_venv` language which uses the `venv` module instead of
  `virtualenv`
    - #631 issue by @dongyuzheng.
    - #739 PR by @ojii.
- Include `LICENSE` in distribution
    - #745 issue by @nicoddemus.
    - #746 PR by @nicoddemus.

### Fixes
- Normalize relative paths for `pre-commit try-repo`
    - #750 PR by @asottile.


1.8.2 - 2018-03-17
==================

### Fixes
- Fix cloning relative paths (regression in 1.7.0)
    - #728 issue by @jdswensen.
    - #729 PR by @asottile.


1.8.1 - 2018-03-12
==================

### Fixes
- Fix integration with go 1.10 and `pkg` directory
    - #725 PR by @asottile
- Restore support for `git<1.8.5` (inadvertantly removed in 1.7.0)
    - #723 issue by @JohnLyman.
    - #724 PR by @asottile.


1.8.0 - 2018-03-11
==================

### Features
- Add a `manual` stage for cli-only interaction
    - #719 issue by @hectorv.
    - #720 PR by @asottile.
- Add a `--multiline` option to `pygrep` hooks
    - #716 PR by @tdeo.


1.7.0 - 2018-03-03
==================

### Features
- pre-commit config validation was split to a separate `cfgv` library
    - #700 PR by @asottile.
- Allow `--repo` to be specified multiple times to autoupdate
    - #658 issue by @KevinHock.
    - #713 PR by @asottile.
- Enable `rev` as a preferred alternative to `sha` in `.pre-commit-config.yaml`
    - #106 issue by @asottile.
    - #715 PR by @asottile.
- Use `--clean-src` option when invoking `nodeenv` to save ~70MB per node env
    - #717 PR by @asottile.
- Refuse to install with `core.hooksPath` set
    - pre-commit/pre-commit-hooks#250 issue by @revolter.
    - #663 issue by @asottile.
    - #718 PR by @asottile.

### Fixes
- hooks with `additional_dependencies` now get isolated environments
    - #590 issue by @coldnight.
    - #711 PR by @asottile.

### Misc
- test against swift 4.x
    - #709 by @theresama.

### Updating

- Run `pre-commit migrate-config` to convert `sha` to `rev` in the
  `.pre-commit-config.yaml` file.


1.6.0 - 2018-02-04
==================

### Features
- Hooks now may have a `verbose` option to produce output even without failure
    - #689 issue by @bagerard.
    - #695 PR by @bagerard.
- Installed hook no longer requires `bash`
    - #699 PR by @asottile.

### Fixes
- legacy pre-push / commit-msg hooks are now invoked as if `git` called them
    - #693 issue by @samskiter.
    - #694 PR by @asottile.
    - #699 PR by @asottile.

1.5.1 - 2018-01-24
==================

### Fixes
- proper detection for root commit during pre-push
    - #503 PR by @philipgian.
    - #692 PR by @samskiter.

1.5.0 - 2018-01-13
==================

### Features
- pre-commit now supports node hooks on windows.
    - for now, requires python3 due to https://bugs.python.org/issue32539
    - huge thanks to @wenzowski for the tip!
    - #200 issue by @asottile.
    - #685 PR by @asottile.

### Misc
- internal reorganization of `PrefixedCommandRunner` -> `Prefix`
    - #684 PR by @asottile.
- https-ify links.
    - pre-commit.com is now served over https.
    - #688 PR by @asottile.


1.4.5 - 2018-01-09
==================

### Fixes
- Fix `local` golang repositories with `additional_dependencies`.
    - #679 #680 issue and PR by @asottile.

### Misc
- Replace some string literals with constants
    - #678 PR by @revolter.

1.4.4 - 2018-01-07
==================

### Fixes
- Invoke `git diff` without a pager during `--show-diff-on-failure`.
    - #676 PR by @asottile.

1.4.3 - 2018-01-02
==================

### Fixes
- `pre-commit` on windows can find pythons at non-hardcoded paths.
    - #674 PR by @asottile.

1.4.2 - 2018-01-02
==================

### Fixes
- `pre-commit` no longer clears `GIT_SSH` environment variable when cloning.
    - #671 PR by @rp-tanium.

1.4.1 - 2017-11-09
==================

### Fixes
- `pre-commit autoupdate --repo ...` no longer deletes other repos.
    - #660 issue by @KevinHock.
    - #661 PR by @KevinHock.

1.4.0 - 2017-11-08
==================

### Features
- Lazily install repositories.
    - When running `pre-commit run <hookid>`, pre-commit will only install
      the necessary repositories.
    - #637 issue by @webknjaz.
    - #639 PR by @asottile.
- Version defaulting now applies to local hooks as well.
    - This extends #556 to apply to local hooks.
    - #646 PR by @asottile.
- Add new `repo: meta` hooks.
    - `meta` hooks expose some linters of the pre-commit configuration itself.
    - `id: check-useless-excludes`: ensures that `exclude` directives actually
      apply to *any* file in the repository.
    - `id: check-hooks-apply`: ensures that the configured hooks apply to
      at least one file in the repository.
    - pre-commit/pre-commit-hooks#63 issue by @asottile.
    - #405 issue by @asottile.
    - #643 PR by @hackedd.
    - #653 PR by @asottile.
    - #654 PR by @asottile.
- Allow a specific repository to be autoupdated instead of all repositories.
    - `pre-commit autoupdate --repo ...`
    - #656 issue by @KevinHock.
    - #657 PR by @KevinHock.

### Fixes
- Apply selinux labelling option to docker volumes
    - #642 PR by @jimmidyson.


1.3.0 - 2017-10-08
==================

### Features
- Add `pre-commit try-repo` commands
    - The new `try-repo` takes a repo and will run the hooks configured in
      that hook repository.
    - An example invocation:
      `pre-commit try-repo https://github.com/pre-commit/pre-commit-hooks`
    - `pre-commit try-repo` can also take all the same arguments as
      `pre-commit run`.
    - It can be used to try out a repository without needing to configure it.
    - It can also be used to test a hook repository while developing it.
    - #589 issue by @sverhagen.
    - #633 PR by @asottile.

1.2.0 - 2017-10-03
==================

### Features
- Add `pygrep` language
    - `pygrep` aims to be a more cross-platform alternative to `pcre` hooks.
    - #630 PR by @asottile.

### Fixes
- Use `pipes.quote` for executable path in hook template
    - Fixes bash syntax error when git dir contains spaces
    - #626 PR by @asottile.
- Clean up hook template
    - Simplify code
    - Fix `--config` not being respected in some situations
    - #627 PR by @asottile.
- Use `file://` protocol for cloning under test
    - Fix `file://` clone paths being treated as urls for golang
    - #629 PR by @asottile.
- Add `ctypes` as an import for virtualenv healthchecks
    - Fixes python3.6.2 <=> python3.6.3 virtualenv invalidation
    - e70825ab by @asottile.

1.1.2 - 2017-09-20
==================

### Fixes
- pre-commit can successfully install commit-msg hooks
    - Due to an oversight, the commit-msg-tmpl was missing from the packaging
    - #623 issue by @sobolevn.
    - #624 PR by @asottile.

1.1.1 - 2017-09-17
==================

### Features
- pre-commit also checks the `ssl` module for virtualenv health
    - Suggestion by @merwok.
    - #619 PR by @asottile.
### Fixes
- pre-commit no longer crashes with unstaged files when run for the first time
    - #620 #621 issue by @Lucas-C.
    - #622 PR by @asottile.

1.1.0 - 2017-09-11
==================

### Features
- pre-commit configuration gains a `fail_fast` option.
    - You must be using the v2 configuration format introduced in 1.0.0.
    - `fail_fast` defaults to `false`.
    - #240 issue by @Lucas-C.
    - #616 PR by @asottile.
- pre-commit configuration gains a global `exclude` option.
    - This option takes a python regular expression and can be used to exclude
      files from _all_ hooks.
    - You must be using the v2 configuration format introduced in 1.0.0.
    - #281 issue by @asieira.
    - #617 PR by @asottile.

1.0.1 - 2017-09-07
==================

### Fixes
- Fix a regression in the return code of `pre-commit autoupdate`
    - `pre-commit migrate-config` and `pre-commit autoupdate` return 0 when
      successful.
    - #614 PR by @asottile.

1.0.0 - 2017-09-07
==================
pre-commit will now be following [semver](https://semver.org/).  Thanks to all
of the [contributors](https://github.com/pre-commit/pre-commit/graphs/contributors)
that have helped us get this far!

### Features

- pre-commit's cache directory has moved from `~/.pre-commit` to
  `$XDG_CACHE_HOME/pre-commit` (usually `~/.cache/pre-commit`).
    - `pre-commit clean` now cleans up both the old and new directory.
    - If you were caching this directory in CI, you'll want to adjust the
      location.
    - #562 issue by @nagromc.
    - #602 PR by @asottile.
- A new configuration format for `.pre-commit-config.yaml` is introduced which
  will enable future development.
    - The new format has a top-level map instead of a top-level list.  The
      new format puts the hook repositories in a `repos` key.
    - Old list-based configurations will continue to be supported.
    - A command `pre-commit migrate-config` has been introduced to "upgrade"
      the configuration format to the new map-based configuration.
    - `pre-commit autoupdate` now automatically calls `migrate-config`.
    - In a later release, list-based configurations will issue a deprecation
      warning.
    - An example diff for upgrading a configuration:

    ```diff
    +repos:
     -   repo: https://github.com/pre-commit/pre-commit-hooks
         sha: v0.9.2
         hooks:
    ```
    - #414 issue by @asottile.
    - #610 PR by @asottile.

### Updating

- Run `pre-commit migrate-config` to convert `.pre-commit-config.yaml` to the
  new map format.
- Update any references from `~/.pre-commit` to `~/.cache/pre-commit`.

0.18.3 - 2017-09-06
===================
- Allow --config to affect `pre-commit install`
- Tweak not found error message during `pre-push` / `commit-msg`
- Improve node support when running under cygwin.

0.18.2 - 2017-09-05
===================
- Fix `--all-files`, detection of staged files, detection of manually edited
  files during merge conflict, and detection of files to push for non-ascii
  filenames.

0.18.1 - 2017-09-04
===================
- Only mention locking when waiting for a lock.
- Fix `IOError` during locking in timeout situtation on windows under python 2.

0.18.0 - 2017-09-02
===================
- Add a new `docker_image` language type.  `docker_image` is intended to be a
  lightweight hook type similar to `system` / `script` which allows one to use
  an existing docker image that provides a hook.  `docker_image` hooks can
  also be used as repository `local` hooks.

0.17.0 - 2017-08-24
===================
- Fix typos in help
- Allow `commit-msg` hook to be uninstalled
- Upgrade the `sample-config`
- Remove undocumented `--no-stash` and `--allow-unstaged-config`
- Remove `validate_config` hook pre-commit hook.
- Fix installation race condition when multiple `pre-commit` processes would
  attempt to install the same repository.

0.16.3 - 2017-08-10
===================
- autoupdate attempts to maintain config formatting.

0.16.2 - 2017-08-06
===================
- Initialize submodules in hook repositories.

0.16.1 - 2017-08-04
===================
- Improve node support when running under cygwin.

0.16.0 - 2017-08-01
===================
- Remove backward compatibility with repositories providing metadata via
  `hooks.yaml`.  New repositories should provide `.pre-commit-hooks.yaml`.
  Run `pre-commit autoupdate` to upgrade to the latest repositories.
- Improve golang support when running under cygwin.
- Fix crash with unstaged trailing whitespace additions while git was
  configured with `apply.whitespace = error`.
- Fix crash with unstaged end-of-file crlf additions and the file's lines
  ended with crlf while git was configured with `core-autocrlf = true`.

0.15.4 - 2017-07-23
===================
- Add support for the `commit-msg` git hook

0.15.3 - 2017-07-20
===================
- Recover from invalid python virtualenvs


0.15.2 - 2017-07-09
===================
- Work around a windows-specific virtualenv bug pypa/virtualenv#1062
  This failure mode was introduced in 0.15.1

0.15.1 - 2017-07-09
===================
- Use a more intelligent default language version for python

0.15.0 - 2017-07-02
===================
- Add `types` and `exclude_types` for filtering files.  These options take
  an array of "tags" identified for each file.  The tags are sourced from
  [identify](https://github.com/chriskuehl/identify).  One can list the tags
  for a file by running `identify-cli filename`.
- `files` is now optional (defaulting to `''`)
- `always_run` + missing `files` also defaults to `files: ''` (previously it
  defaulted to `'^$'` (this reverses e150921c).

0.14.3 - 2017-06-28
===================
- Expose `--origin` and `--source` as `PRE_COMMIT_ORIGIN` and
  `PRE_COMMIT_SOURCE` environment variables when running as `pre-push`.

0.14.2 - 2017-06-09
===================
- Use `--no-ext-diff` when running `git diff`

0.14.1 - 2017-06-02
===================
- Don't crash when `always_run` is `True` and `files` is not provided.
- Set `VIRTUALENV_NO_DOWNLOAD` when making python virtualenvs.

0.14.0 - 2017-05-16
===================
- Add a `pre-commit sample-config` command
- Enable ansi color escapes on modern windows
- `autoupdate` now defaults to `--tags-only`, use `--bleeding-edge` for the
  old behavior
- Add support for `log_file` in hook configuration to tee hook output to a
  file for CI consumption, etc.
- Fix crash with unicode commit messages during merges in python 2.
- Add a `pass_filenames` option to allow disabling automatic filename
  positional arguments to hooks.

0.13.6 - 2017-03-27
===================
- Fix regression in 0.13.5: allow `always_run` and `files` together despite
  doing nothing.

0.13.5 - 2017-03-26
===================
- 0.13.4 contained incorrect files

0.13.4 - 2017-03-26
===================
- Add `--show-diff-on-failure` option to `pre-commit run`
- Replace `jsonschema` with better error messages

0.13.3 - 2017-02-23
===================
- Add `--allow-missing-config` to install: allows `git commit` without a
  configuration.

0.13.2 - 2017-02-17
===================
- Version the local hooks repo
- Allow `minimum_pre_commit_version` for local hooks

0.13.1 - 2017-02-16
===================
- Fix dummy gem for ruby local hooks

0.13.0 - 2017-02-16
===================
- Autoupdate now works even when the current state is broken.
- Improve pre-push fileset on new branches
- Allow "language local" hooks, hooks which install dependencies using
  `additional_dependencies` and `language` are now allowed in `repo: local`.

0.12.2 - 2017-01-27
===================
- Fix docker hooks on older (<1.12) docker

0.12.1 - 2017-01-25
===================
- golang hooks now support additional_dependencies
- Added a --tags-only option to pre-commit autoupdate

0.12.0 - 2017-01-24
===================
- The new default file for implementing hooks in remote repositories is now
  .pre-commit-hooks.yaml to encourage repositories to add the metadata.  As
  such, the previous hooks.yaml is now deprecated and generates a warning.
- Fix bug with local configuration interfering with ruby hooks
- Added support for hooks written in golang.

0.11.0 - 2017-01-20
===================
- SwiftPM support.

0.10.1 - 2017-01-05
===================
- shlex entry of docker based hooks.
- Make shlex behaviour of entry more consistent.

0.10.0 - 2017-01-04
===================
- Add an `install-hooks` command similar to `install --install-hooks` but
  without the `install` side-effects.
- Adds support for docker based hooks.

0.9.4 - 2016-12-05
==================
- Warn when cygwin / python mismatch
- Add --config for customizing configuration during run
- Update rbenv + plugins to latest versions
- pcre hooks now fail when grep / ggrep are not present

0.9.3 - 2016-11-07
==================
- Fix python hook installation when a strange setup.cfg exists

0.9.2 - 2016-10-25
==================
- Remove some python2.6 compatibility
- UI is no longer sized to terminal width, instead 80 characters or longest
  necessary width.
- Fix inability to create python hook environments when using venv / pyvenv on
  osx

0.9.1 - 2016-09-10
==================
- Remove some python2.6 compatibility
- Fix staged-files-only with external diff tools

0.9.0 - 2016-08-31
==================
- Only consider forward diff in changed files
- Don't run on staged deleted files that still exist
- Autoupdate to tags when available
- Stop supporting python2.6
- Fix crash with staged files containing unstaged lines which have non-utf8
  bytes and trailing whitespace

0.8.2 - 2016-05-20
==================
- Fix a crash introduced in 0.8.0 when an executable was not found

0.8.1 - 2016-05-17
==================
- Fix regression introduced in 0.8.0 when already using rbenv with no
  configured ruby hook version

0.8.0 - 2016-04-11
==================
- Fix --files when running in a subdir
- Improve --help a bit
- Switch to pyterminalsize for determining terminal size

0.7.6 - 2016-01-19
==================
- Work under latest virtualenv
- No longer create empty directories on windows with latest virtualenv

0.7.5 - 2016-01-15
==================
- Consider dead symlinks as files when committing

0.7.4 - 2016-01-12
==================
- Produce error message instead of crashing on non-utf8 installation failure

0.7.3 - 2015-12-22
==================
- Fix regression introduced in 0.7.1 breaking `git commit -a`

0.7.2 - 2015-12-22
==================
- Add `always_run` setting for hooks to run even without file changes.

0.7.1 - 2015-12-19
==================
- Support running pre-commit inside submodules

0.7.0 - 2015-12-13
==================
- Store state about additional_dependencies for rollforward/rollback compatibility

0.6.8 - 2015-12-07
==================
- Build as a universal wheel
- Allow '.format('-like strings in arguments
- Add an option to require a minimum pre-commit version

0.6.7 - 2015-12-02
==================
- Print a useful message when a hook id is not present
- Fix printing of non-ascii with unexpected errors
- Print a message when a hook modifies files but produces no output

0.6.6 - 2015-11-25
==================
- Add `additional_dependencies` to hook configuration.
- Fix pre-commit cloning under git 2.6
- Small improvements for windows

0.6.5 - 2015-11-19
==================
- Allow args for pcre hooks

0.6.4 - 2015-11-13
==================
- Fix regression introduced in 0.6.3 regarding hooks which make non-utf8 diffs

0.6.3 - 2015-11-12
==================
- Remove `expected_return_code`
- Fail a hook if it makes modifications to the working directory

0.6.2 - 2015-10-14
==================
- Use --no-ri --no-rdoc instead of --no-document for gem to fix old gem

0.6.1 - 2015-10-08
==================
- Fix pre-push when pushing something that's already up to date

0.6.0 - 2015-10-05
==================
- Filter hooks by stage (commit, push).

0.5.5 - 2015-09-04
==================
- Change permissions a few files
- Rename the validate entrypoints
- Add --version to some entrypoints
- Add --no-document to gem installations
- Use expanduser when finding the python binary
- Suppress complaint about $TERM when no tty is attached
- Support pcre hooks on osx through ggrep

0.5.4 - 2015-07-24
==================
- Allow hooks to produce outputs with arbitrary bytes
- Fix pre-commit install when .git/hooks/pre-commit is a dead symlink
- Allow an unstaged config when using --files or --all-files

0.5.3 - 2015-06-15
==================
- Fix autoupdate with "local" hooks - don't purge local hooks.

0.5.2 - 2015-06-02
==================
- Fix autoupdate with "local" hooks

0.5.1 - 2015-05-23
==================
- Fix bug with unknown non-ascii hook-id
- Avoid crash when .git/hooks is not present in some git clients

0.5.0 - 2015-05-19
==================
- Add a new "local" hook type for running hooks without remote configuration.
- Complain loudly when .pre-commit-config.yaml is unstaged.
- Better support for multiple language versions when running hooks.
- Allow exclude to be defaulted in repository configuration.

0.4.4 - 2015-03-29
==================
- Use sys.executable when executing virtualenv

0.4.3 - 2015-03-25
==================
- Use reset instead of checkout when checkout out hook repo

0.4.2 - 2015-02-27
==================
- Limit length of xargs arguments to workaround windows xargs bug

0.4.1 - 2015-02-27
==================
- Don't rename across devices when creating sqlite database

0.4.0 - 2015-02-27
==================
- Make ^C^C During installation not cause all subsequent runs to fail
- Print while installing (instead of while cloning)
- Use sqlite to manage repositories (instead of symlinks)
- MVP Windows support

0.3.6 - 2015-02-05
==================
- `args` in venv'd languages are now property quoted.

0.3.5 - 2015-01-15
==================
- Support running during `pre-push`.  See https://pre-commit.com/#advanced 'pre-commit during push'.

0.3.4 - 2015-01-13
==================
- Allow hook providers to default `args` in `hooks.yaml`

0.3.3 - 2015-01-06
==================
- Improve message for `CalledProcessError`

0.3.2 - 2014-10-07
==================
- Fix for `staged_files_only` with color.diff = always #176.

0.3.1 - 2014-10-03
==================
- Fix error clobbering #174.
- Remove dependency on `plumbum`.
- Allow pre-commit to be run from anywhere in a repository #175.

0.3.0 - 2014-09-18
==================
- Add `--files` option to `pre-commit run`

0.2.11 - 2014-09-05
===================
- Fix terminal width detection (broken in 0.2.10)

0.2.10 - 2014-09-04
===================
- Bump version of nodeenv to fix bug with ~/.npmrc
- Choose `python` more intelligently when running.

0.2.9 - 2014-09-02
==================
- Fix bug where sys.stdout.write must take `bytes` in python 2.6

0.2.8 - 2014-08-13
==================
- Allow a client to have duplicates of hooks.
- Use --prebuilt instead of system for node.
- Improve some fatal error messages

0.2.7 - 2014-07-28
==================
- Produce output when running pre-commit install --install-hooks

0.2.6 - 2014-07-28
==================
- Print hookid on failure
- Use sys.executable for running nodeenv
- Allow running as `python -m pre_commit`

0.2.5 - 2014-07-17
==================
- Default columns to 80 (for non-terminal execution).

0.2.4 - 2014-07-07
==================
- Support --install-hooks as an argument to `pre-commit install`
- Install hooks before attempting to run anything
- Use `python -m nodeenv` instead of `nodeenv`

0.2.3 - 2014-06-25
==================
- Freeze ruby building infrastructure
- Fix bug that assumed diffs were utf-8

0.2.2 - 2014-06-22
==================
- Fix filenames with spaces

0.2.1 - 2014-06-18
==================
- Use either `pre-commit` or `python -m pre_commit.main` depending on which is
  available
- Don't use readlink -f

0.2.0 - 2014-06-17
==================
- Fix for merge-conflict during cherry-picking.
- Add -V / --version
- Add migration install mode / install -f / --overwrite
- Add `pcre` "language" for perl compatible regexes
- Reorganize packages.

0.1.1 - 2014-06-11
==================
- Fixed bug with autoupdate setting defaults on un-updated repos.

0.1.0 - 2014-06-07
==================
- Initial Release
