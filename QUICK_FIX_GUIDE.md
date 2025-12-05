# Quick Fix Guide: Template Not Appearing

## Most Likely Issue: Folder Structure for Configuration Repositories

If you're using **Configuration Repository** method, AMP might expect files in a subfolder structure.

### Fix 1: Reorganize Repository Structure

Your repository currently has files at the root. For Configuration Repositories, they might need to be in a subfolder:

**Current (may not work):**
```
repository-root/
  nzp.kvp
  nzpconfig.json
  nzpmetaconfig.json
  manifest.json
```

**Try This Structure:**
```
repository-root/
  templates/
    nzp/
      nzp.kvp
      nzpconfig.json
      nzpmetaconfig.json
      nzpports.json
      nzpupdates.json
  manifest.json (at root)
  README.md
```

Then commit and push, and re-fetch in AMP.

### Fix 2: Use Deployment Templates Method Instead

**EASIER OPTION** - Use manual file placement:

1. Copy these files to: `ADS/Plugins/ADSModule/DeploymentTemplates/`
   - `nzp.kvp`
   - `nzpconfig.json`
   - `nzpmetaconfig.json`

2. Files should be **directly in that folder** (no subfolders)

3. **Restart AMP service** (full restart, not just refresh)

4. In AMP web interface:
   - Go to **Configuration** → **Instance Deployment**
   - Click **"Fetch Latest"**
   - Wait for completion
   - **Refresh browser page** (F5)

5. Try creating a new instance - template should appear

### Fix 3: Check for AMP Settings

Some AMP versions have settings that hide custom templates:

1. Check **Configuration** → **Instance Deployment** settings
2. Look for options like:
   - "Show only official templates"
   - "Hide community templates"
   - Any filter settings

### Fix 4: Verify File Location

**For Configuration Repository**, files should end up in:
```
Plugins/GenericModule/templates/nzp/
```

**For Deployment Templates**, files should be in:
```
ADS/Plugins/ADSModule/DeploymentTemplates/
```

Make sure you're checking the right location!

## Recommended Action

**Try Fix 2 first** (Deployment Templates method) - it's the most reliable and doesn't require repository changes.

If that works, then we know the issue is with the Configuration Repository structure and can fix that separately.

