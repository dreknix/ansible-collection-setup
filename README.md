# Ansible Collection for Setup Computers

A collection of roles for configuring all Linux hosts. The roles are currently
only supporting Debian or Ubuntu based distros.

## Usage

Configure `collections_path` in `ansible.cfg`.

Insert collection into `requirements.yml`:

```yaml
collections:
  - name: docker
    source: git@github.com:dreknix/ansible-collection-setup.git
    type: git
    version: main
```

Use Galaxy to install the collection:

```console
$ ansible-galaxy install --force-with-deps -r requirements.yml
```

Import the playbook of the collection and overwrite the default values of the
variables:

```yaml
- name: Setup computers
  ansible.builtin.import_playbook: dreknix.setup.playbook
  vars:
    keyboard_model: "pc105"
    keyboard_layout: "de"
    keyboard_variant: "nodeadkeys"

    locale_lang: "en_US.UTF-8"
    locale_list: ["{{ locale_lang }}"]

    timezone: "Europe/Berlin"
```

## Roles

The following roles are available.

### Hostname

Set the host name to the Ansible variable `inventory_hostname`.

* **Tag**: `setup_hostname`
* **Variables**:

### Keyboard

Configure the keyboard layout.

* **Tag**: `setup_keyboard`
* **Variables**:
  * `keyboard_model`: `pc104`
  * `keyboard_layout`: `us`
  * `keyboard_variant`: `''`
  * `keyboard_options`: `''`
  * `keyboard_backspace`: `guess`

### Locale

Configure the locale settings.

* **Tag**: `setup_locale`
* **Variables**:
  * `locale_list`: `[en_GB.UTF-8, en_US.UTF-8]`
  * `locale_lang`: `en_US.UTF-8`
  * ...

### Timezone

Set the time zone.

* **Tag**: `setup_timezone`
* **Variables**:
  * `timezone`: `Europe/London`

### Upgrade

Upgrade all packages.

* **Tag**: `setup_upgrade`
* **Variables**:

## License

[MIT](https://github.com/dreknix/ansible-collection-setup/blob/main/LICENSE)
