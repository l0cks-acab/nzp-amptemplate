# Troubleshooting: Template Not Appearing in AMP

## The Problem
Template files are in the correct places but not showing up in "Create Instance" list.

## Common Causes & Solutions

### 1. **Configuration Repository Structure Issue** ⚠️

AMP Configuration Repositories might expect templates in a **subfolder structure**, not at the repository root.

**Current Structure (may be wrong):**
```
repository-root/
  nzp.kvp
  nzpconfig.json
  nzpmetaconfig.json
  manifest.json
  README.md
```

**Expected Structure (for Configuration Repositories):**
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

### 2. **Wrong Location for Configuration Repositories**

Configuration Repositories place templates in:
- `Plugins/GenericModule/templates/nzp/`

But Deployment Templates (manual method) go in:
- `ADS/Plugins/ADSModule/DeploymentTemplates/`

**Make sure you're checking the right location!**

### 3. **Template Needs to be in Subfolder**

According to AMP docs, Configuration Repository templates should be organized in folders by template name.

## Solutions to Try

### Solution 1: Check Current File Location
Ask yourself: Where exactly are the files right now?
- `ADS/Plugins/ADSModule/DeploymentTemplates/` (Deployment Templates - Method 1)
- `Plugins/GenericModule/templates/nzp/` (Configuration Repository)
- Somewhere else?

### Solution 2: Reorganize Repository Structure
If using Configuration Repository, move files to a subfolder structure:

```
nzp/
  nzp.kvp
  nzpconfig.json
  nzpmetaconfig.json
  nzpports.json
  nzpupdates.json
```

OR

```
templates/
  nzp/
    nzp.kvp
    nzpconfig.json
    nzpmetaconfig.json
    nzpports.json
    nzpupdates.json
```

### Solution 3: Use Deployment Templates Instead
If Configuration Repository is causing issues, use the manual method:
1. Copy files to `ADS/Plugins/ADSModule/DeploymentTemplates/`
2. Files should be directly in that folder (no subfolders)
3. Restart AMP service
4. Refresh templates in web interface

### Solution 4: Check Manifest.json Location
The manifest.json might need to reference the subfolder structure if files are in a subfolder.

### Solution 5: Verify AMP Settings
- Go to **Configuration** → **Instance Deployment**
- Make sure no filters are hiding the template
- Check if there's a "Show only official templates" option that's enabled

### Solution 6: Restart AMP Service
Sometimes AMP needs a full restart to recognize new templates:
1. Stop AMP service
2. Wait 10 seconds
3. Start AMP service
4. Go to web interface and refresh templates

## Quick Diagnostic Checklist

- [ ] Files are in `ADS/Plugins/ADSModule/DeploymentTemplates/` (if using Method 1)
- [ ] Files are in `Plugins/GenericModule/templates/nzp/` (if using Configuration Repository)
- [ ] All required files are present (nzp.kvp, nzpconfig.json, nzpmetaconfig.json)
- [ ] File names match exactly (case-sensitive)
- [ ] AMP service has been restarted
- [ ] Templates have been refreshed in web interface
- [ ] Browser page has been refreshed (F5)
- [ ] No filters are hiding the template in the interface
- [ ] Template files are valid JSON/KVP format
- [ ] File permissions allow AMP to read the files

## Next Steps

1. **Tell me exactly where the files are located** (full path)
2. **Which method are you using?** (Configuration Repository or Deployment Templates)
3. **Have you restarted the AMP service?**
4. **What does the "Create Instance" list show?** (is it empty or showing other templates?)

