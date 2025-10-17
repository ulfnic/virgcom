# virgcom

Proof of concept

An "sshless" `virsh` wrapper that executes a command inside a guest, then repeats the stdout, stderr and exit code on the host.

Requires `qemu-guest-agent` installed on the guest. `virsh`, `jq` and `base64` installed on the host.

```bash
# Output help
virgcom --help
```
```bash
virgcom [ARGUEMENT...]

	Proof of concept

	An "sshless" virsh wrapper that executes a command inside a guest,
	then repeats the stdout, stderr and exit code on the host.

DEPENDENCIES
	virsh jq base64

ARGUEMENT
	-d|--domain DOMAIN          Domain of VM
	-c|--command COMMAND        String to execute using: bash -c
	-S|--send-only              Only send the command
	-r|--retry-max COUNT        Wait for process to finish COUNT times, default: 100
	-s|--retry-speed SECONDS    Time between retries, default: 0.1
	-k|--kill-after-max-retry   kill -9 process inside VM if max retries is exceeded
	-v|--verbose                Verbose output
	-h|--help                   Print help doc

ENVIRONMENT
	DEBUG                       Use set -x to print debugging information

EXAMPLES
	virgcom -d my_vm -c 'free -h'
```
