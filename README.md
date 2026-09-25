# ansible-ssh

Configures OpenSSH on RHEL-family hosts and enables `sshd` at boot without
starting it during image construction. Configuration changes restart `sshd`
only when it is running.

## Variables

- `ssh_password_authentication`: `false` by default; when `true`, requires a
  public key followed by a password for ordinary users.
- `ssh_keyboard_interactive_group`: `keyboard-interactive` by default; members
  can use public-key plus keyboard-interactive authentication.
- `ssh_keyboard_interactive_excluded_cidrs`: optional non-empty list of IPv4 or
  IPv6 CIDRs; disables keyboard-interactive authentication for that group from
  those networks.

## Firewalld integration

When `/etc/firewalld/policies` exists, the role owns `ssh-host.xml` there. Its
`ANY` → `HOST` policy grants the firewalld `ssh` service (TCP/22) from every
zone for both IP families at priority `-1`. Other traffic continues to later
policies and zones. A zone-to-`HOST` policy with a lower priority, such as `-2`,
can restrict new SSH connections from that zone; a rule inside the zone cannot
reverse this grant.

The role does not install or depend on firewalld. It validates the assembled
firewalld configuration after changing its policy and reloads firewalld only
when the service is running. Include the policy before first boot on images
that require SSH access.
