### Hosteur backup Dashboard Credential

**Backup Dashboard**: [https://node${nodes.hosteur-rag-backup-ui.master.id}-${env.domain}](https://node${nodes.hosteur-rag-backup-ui.master.id}-${env.domain}:8443/)  
**Username**: ${globals.UI_USER}  
**Password**: ${globals.UI_PASS} 

**Backup Encryption Key**: ${globals.BK_KEY}
**!! Keep this key to restore backup anytime!!**

The provided credentials can be used to access all agent backup deployed on this environment.