# gh-repo-export

A `gh` extension to generate [GitHub organization repository migrations](https://docs.github.com/en/enterprise-cloud@latest/rest/migrations/orgs).

## Quickstart

1. Download and install [jq](https://stedolan.github.io/jq/download/)
1. `gh extension install andyfeller/gh-repo-export`
1. `gh repo-export <organization> <repo> ...`
1. Profit! :moneybag: :money_with_wings: :money_mouth_face: :money_with_wings: :moneybag:

## Usage

> **Note**
> `gh-repo-export` requires the use of coarse-grained v1 PAT token with `repo` and `admin:org` scopes.

```shell
$ gh repo-export --help

Bulk exports a list of Git repositories from an organization

USAGE
  gh repo-export [flags] <organization> <repo1> <repo2> ... <repoN>
  gh repo-export [flags] <organization> <path/to/repos file>

FLAGS
      --archive=string                Name of archive excluding extension; default 'migration-archive-<migration_id>'
      --archive-per-repo              Generates 1 archive per repository instead of 1 archive for all repositories
  -d, --debug                         Enable debugging
      --exclude-attachments           Indicates attachments should be excluded from the migration
      --exclude-git-data              Indicates git data should be excluded from the migration
      --exclude-metadata              Indicates metadata should be excluded from the migration
      --exclude-owner-projects        Indicates projects owned by the organization or users should be excluded from the migration
      --exclude-releases              Indicates releases should be excluded from the migration
  -h, --help                          Display help usage
      --hostname=string               Hostname of the GitHub instance to authenticate with
      --lock-repositories             Indicates repositories should be locked (to prevent manipulation) while migrating data
      --skip-download                 Skip downloading the archive(s), instead outputting the URL(s) to stdout (curl and sed required)

EXAMPLES
  # Generate 1 archive containing test1 repository, reading repositories from arguments
  $ gh repo-export tinyfists test1

  # Generate 1 archive containing both test1 and test2 repositories, reading repositories from arguments
  $ gh repo-export tinyfists test1 test2

  # Generate 1 archive containing both test1 and test2 repositories, reading repositories from arguments, and output the archive URL instead of downloading
  $ gh repo-export --skip-download tinyfists test1 test2

  # Generate 2 archives, 1 containing test1 repository and 1 containing test2 repository, reading repositories from arguments
  $ gh repo-export --archive-per-repo tinyfists test1 test2

  # Generate 2 archives, 1 containing test1 repository and 1 containing test2 repository, reading repositories from 'repos.txt' file
  $ gh repo-export --archive-per-repo tinyfists repos.txt
```

### Examples

<details><summary><b><code>$ gh repo-export tinyfists issue-driven-github-admin</code></b></summary>
<p>

```shell
Reading repositories from arguments: issue-driven-github-admin
Starting migration 3431913 for repositories: issue-driven-github-admin
Watching migration 3431913 with 'exporting' state
Watching migration 3431913 with 'exporting' state
Watching migration 3431913 with 'exporting' state
Watching migration 3431913 with 'exported' state
Downloading migration 3431913 archive to migration-archive-3431913.tar.gz
```
</p>
</details>

<details><summary><b><code>$ gh repo-export tinyfists issue-driven-github-admin actions-experiments</code></b></summary>
<p>

```shell
Reading repositories from arguments: issue-driven-github-admin actions-experiments
Starting migration 3431922 for repositories: issue-driven-github-admin actions-experiments
Watching migration 3431922 with 'exporting' state
Watching migration 3431922 with 'exporting' state
Watching migration 3431922 with 'exporting' state
Watching migration 3431922 with 'exporting' state
Watching migration 3431922 with 'exported' state
Downloading migration 3431922 archive to migration-archive-3431922.tar.gz
```
</p>
</details>

<details><summary><b><code>$ gh repo-export --skip-download tinyfists issue-driven-github-admin actions-experiments</code></b></summary>
<p>

```shell
Reading repositories from arguments: issue-driven-github-admin actions-experiments
Starting migration 3431922 for repositories: issue-driven-github-admin actions-experiments
Watching migration 3431922 with 'exporting' state
Watching migration 3431922 with 'exporting' state
Watching migration 3431922 with 'exporting' state
Watching migration 3431922 with 'exporting' state
Watching migration 3431922 with 'exported' state
Archive URL for migration 3762306: https://github-cloud.s3.amazonaws.com/migration/...
```
</p>
</details>

<details><summary><b><code>$ gh repo-export --archive-per-repo tinyfists issue-driven-github-admin actions-experiments</code></b></summary>
<p>

```shell
Reading repositories from arguments: issue-driven-github-admin actions-experiments
Starting migration 3431937 for repositories: issue-driven-github-admin
Starting migration 3431938 for repositories: actions-experiments
Watching migration 3431937 with 'exporting' state
Watching migration 3431938 with 'exporting' state
Watching migration 3431937 with 'exporting' state
Watching migration 3431938 with 'exported' state
Watching migration 3431937 with 'exporting' state
Watching migration 3431937 with 'exported' state
Downloading migration 3431937 archive to migration-archive-3431937.tar.gz
Downloading migration 3431938 archive to migration-archive-3431938.tar.gz
```
</p>
</details>

<details><summary><b><code>$ gh repo-export tinyfists repos.txt</code></b></summary>
<p>

```shell
Reading repositories from file: repos.txt
Starting migration 3431982 for repositories:  issue-driven-github-admin actions-experiments
Watching migration 3431982 with 'exporting' state
Watching migration 3431982 with 'exporting' state
Watching migration 3431982 with 'exporting' state
Watching migration 3431982 with 'exported' state
Downloading migration 3431982 archive to migration-archive-3431982.tar.gz
```
</p>
</details>

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
