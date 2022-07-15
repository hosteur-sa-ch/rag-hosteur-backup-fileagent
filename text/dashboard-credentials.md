### Hosteur backup Dashboard : Credentials

* **Backup Dashboard**: [https://node${nodes.hosteur-rag-backup-ui.master.id}-${env.domain}:8443](https://node${nodes.hosteur-rag-backup-ui.master.id}-${env.domain}:8443/)

* **Username**: ${globals.UI_USER}

* **Password**: ${globals.UI_PASS}

**Backup Encryption Key (AES-256)**: ${globals.BK_KEY}

**!! Keep this key to restore your backups at anytime !!**

These credentials can be used to access all agent backups deployed on this environment.

**You are now ready to deploy Hosteur Backup File Agent on a node from the Marketplace or from Node's Addons**