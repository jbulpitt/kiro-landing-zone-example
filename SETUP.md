# How this was set up

Kiro CLI on a Linux machine, using the free tier. No AWS account or AWS credentials
were needed, and nothing was deployed.

Versions used: Kiro CLI 2.35.1, Terraform 1.17.1.

## 1. Install the Kiro CLI

```bash
curl -fsSL https://cli.kiro.dev/install | bash
kiro-cli --version
```

## 2. Sign in (free tier)

```bash
kiro-cli login --license free --use-device-flow
kiro-cli whoami
```

The free license signs in with an AWS Builder ID (or Google or GitHub). The device flow
prints a code to approve in a browser, which suits a machine without a desktop. On a
laptop, `kiro-cli login` opens the browser directly.

## 3. Write a spec

[SPEC.md](SPEC.md) is the only input: one page describing the resources, the files to
write and the rules to follow.

## 4. Let Kiro implement the spec

```bash
kiro-cli chat --no-interactive --trust-tools=fs_read,fs_write "Read SPEC.md and implement it."
```

- `--no-interactive` runs the request once and exits.
- `--trust-tools=fs_read,fs_write` lets Kiro read and write files without asking.
  Other tools, such as running shell commands, are not pre-approved.

Run plain `kiro-cli chat` for the interactive mode, where Kiro asks before each tool use.

## 5. Check the result without deploying

```bash
terraform fmt -check
terraform init -backend=false
terraform validate
```

`init -backend=false` downloads the AWS provider only. No plan or apply was run, and
the machine has no AWS credentials.
