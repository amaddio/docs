# Deadsnakes Ansible Playbook

Here is an example Ansible Playbook to add the Deadsnakes PPA repository.

## Playbook

```yaml
  ---
  - name: Add Deadsnakes Nightly APT repository
    apt_repository:
      repo: ppa:deadsnakes/nightly
    when: ansible_distribution_release in ["noble", "jammy", "focal"]

  - name: Install latest deadsnakes python
    apt:
      name: ['python3.9-dev', 'python3.9-venv', 'python3.10-dev', 'python3.10-venv', 'python3.11-dev', 'python3.11-venv', 'python3.12-dev', 'python3.12-venv']
      state: latest
      update_cache: yes
    when: ansible_distribution_release in ["noble", "jammy", "focal"]
```

This will need to be updated as new Ubuntu LTS releases come out and new Python versions.
