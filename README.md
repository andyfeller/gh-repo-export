# gh-repo-export

A `gh` extension to generate GitHub repository migrations.

## Quickstart

1. Download and install [jq](https://stedolan.github.io/jq/download/)
1. `gh extension install andyfeller/gh-repo-export`
1. `gh repo-export <organization> <repo> ...`
1. Profit! :moneybag: :money_with_wings: :money_mouth_face: :money_with_wings: :moneybag:

## Usage

```shell
$ gh repo-export --help

Bulk exports a list of Git repositories from an organization

USAGE
  gh-repo-export [options] <organization> <repo> ...

FLAGS
  -d, --debug                         Enable debugging
      --exclude-attachments           Indicates attachments should be excluded from the migration
      --exclude-releases              Indicates releases should be excluded from the migration
      --exclude-owner-projects        Indicates projects owned by the organization or users should be excluded from the migration
      --lock-repositories             Indicates repositories should be locked (to prevent manipulation) while migrating data
```

## Setup

Like any other `gh` CLI extension, `gh-repo-export` is trivial to install or upgrade and works on most operating systems:

- **Installation**

  ```shell
  gh extension install andyfeller/gh-repo-export
  ```
  
  _For more information: [`gh extension install`](https://cli.github.com/manual/gh_extension_install)_

- **Upgrade**

  ```shell
  gh extension upgrade gh-repo-export
  ```

  _For more information: [`gh extension upgrade`](https://cli.github.com/manual/gh_extension_upgrade)_
