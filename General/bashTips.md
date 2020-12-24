# Bash Tips

## Quick Setup of package.json

```bash
npm init -y
```

## Upgrading Node with NVM

1. Check current node version

   ```bash
   nvm ls
   ```

2. Installing latest node

   ```bash
   nvm install node
   ```

3. Migrating globally installed packages

   ```bash
   nvm reinstall-packages v13.12.0
   ```

4. Check list of globally installed packages

   ```bash
   npm list -g --depth 0
   ```
