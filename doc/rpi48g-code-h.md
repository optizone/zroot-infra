# RPI FLAT

## Железо

RaspberryPi 4B+ 8Gb

## Описание

VM's:

- OpenMediaVault:
  - SMB:
    - backups
    - media

- haos:
  - mqtt
  - zigbee2mqtt
  - adguard
  - grocy

### Стратегия бекапов и хранения данных

Offsite:

- smb-thinkpad-backups (once a week)
- smb-thinkpad-disk-images (rsync)

Onsite:

- smb-rpi48g-code-h-backups (once a week)
- smb-thinkpad-disk-images
