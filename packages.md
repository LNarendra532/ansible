✅ Recommended: Use the package module (cross-platform)

- name: Install a package (cross-platform)
  hosts: all
  become: yes
  tasks:
    - name: Install nginx
      package:
        name: nginx
        state: present

This will:

    Use apt on Debian/Ubuntu

    Use yum or dnf on RHEL/CentOS/Fedora

    Use zypper on openSUSE/SLES

👇 You can also use distro-specific modules if needed:
On Debian/Ubuntu (APT-based)

- name: Install nginx on Ubuntu
  apt:
    name: nginx
    state: present
    update_cache: yes

On RHEL/CentOS (YUM-based)

- name: Install nginx on CentOS
  yum:
    name: nginx
    state: present

On Fedora (DNF)

- name: Install nginx on Fedora
  dnf:
    name: nginx
    state: present

📌 Additional Options

    To install multiple packages:

- name: Install multiple packages
  package:
    name:
      - nginx
      - git
      - curl
    state: present

To install a specific version:

- name: Install a specific version of nginx
  package:
    name: nginx-1.18.0
    state: present

To ensure a package is removed:

    - name: Remove nginx
      package:
        name: nginx
        state: absent

Let me know your target OS or package if you want a tailored example.
You said:
what is present , installed and absent , latest
ChatGPT said:

In Ansible, when you install or manage packages using modules like package, apt, yum, etc., you specify the state parameter to define what should happen to the package.

Here's what each state means:
✅ present

    Ensures that the package is installed.

    If it's already installed (any version), nothing changes.

    If it's not installed, Ansible will install it.

- name: Ensure nginx is installed
  package:
    name: nginx
    state: present

✅ installed

    Alias for present.

    Works the same way.

    Included for readability or personal preference.

# Same as state: present
- name: Ensure nginx is installed
  package:
    name: nginx
    state: installed

❌ absent

    Ensures the package is removed (uninstalled).

    If it's already not installed, Ansible does nothing.

- name: Remove nginx
  package:
    name: nginx
    state: absent

🔄 latest

    Ensures the package is installed and updated to the latest version available from the package manager.

    If the latest version is already installed, no change.

    If an older version is installed, it will be upgraded.

- name: Install or upgrade nginx to the latest version
  package:
    name: nginx
    state: latest

Summary Table
State	Description
present	Ensure the package is installed
installed	Same as present
absent	Ensure the package is removed
latest	Ensure the latest version of the package is installed

Let me know if you'd like examples for specific operating systems or use cases (like pinning a version or using repositories).