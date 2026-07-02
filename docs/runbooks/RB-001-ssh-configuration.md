# RB-001 - SSH Configuration

## Cel

Bezpieczna konfiguracja usługi SSH.

## Zmiany

Przed każdą zmianą wykonywana jest kopia:

/root/backups/ssh/sshd_config-YYYY-MM-DD.bak

## Przywracanie

cp /root/backups/ssh/sshd_config-YYYY-MM-DD.bak /etc/ssh/sshd_config

systemctl restart ssh

## Verification

After generating a new SSH key:

- verify the fingerprint,
- record it in the password manager (or another secure location),
- confirm the key is dedicated to a single environment.

## 
Never terminate the current administrative session until a new authentication method has been successfully verified in a separate session.