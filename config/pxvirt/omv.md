# OpenMediaVault

## Установка ARM64

[Ссылка](https://docs.openmediavault.org/en/stable/installation/on_debian.html)
на инструкцию по установке.

Установка происходит на Debian 12.

> [!NOTE]
> Не забыть обновить систему и перезагрузиться перед началом установки.\
> Если подключение по ssh не к руту: использовать `su -`, а не просто `su`.

```Bash
# NOTE: if dropping from ssh user to root using `su` dont forget -: `su -`

apt-get install --yes gnupg
wget --quiet \
    --output-document=- \
    https://packages.openmediavault.org/public/archive.key | \
    gpg --dearmor --yes --output "/usr/share/keyrings/openmediavault-archive-keyring.gpg"
echo deb [signed-by=/usr/share/keyrings/openmediavault-archive-keyring.gpg] https://packages.openmediavault.org/public sandworm main > /etc/apt/sources.list.d/openmediavault.list

export LANG=C.UTF-8
export DEBIAN_FRONTEND=noninteractive
export APT_LISTCHANGES_FRONTEND=none
apt-get update
apt-get --yes --auto-remove --show-upgraded \
    --allow-downgrades --allow-change-held-packages \
    --no-install-recommends \
    --option DPkg::Options::="--force-confdef" \
    --option DPkg::Options::="--force-confold" \
    install openmediavault


omv-confdbadm populate
omv-salt deploy run systemd-networkd
```

После можно открывать в браузере по IP адресу хоста, без указания порта. Логин и
пароль по-умолчанию: `admin` и `openmediavault`.
