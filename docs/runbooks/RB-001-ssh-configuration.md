# RB-001 - SSH Configuration

## Cel

Bezpieczna konfiguracja usługi SSH.

## Zmiany

Przed każdą zmianą wykonywana jest kopia:

/root/backups/ssh/sshd_config-YYYY-MM-DD.bak

## Przywracanie

cp /root/backups/ssh/sshd_config-YYYY-MM-DD.bak /etc/ssh/sshd_config

systemctl restart ssh