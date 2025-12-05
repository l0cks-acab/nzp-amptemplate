# Diagnostic Checklist: Template Not Appearing

## Critical Questions to Answer

### 1. Where are the files located?
Please check and tell me the **exact path**:
- [ ] `ADS/Plugins/ADSModule/DeploymentTemplates/` (Deployment Templates method)
- [ ] `Plugins/GenericModule/templates/nzp/` (Configuration Repository method)
- [ ] Other location? _______________

### 2. Which method are you using?
- [ ] Configuration Repository (you added the GitHub repo)
- [ ] Deployment Templates (manually placed files)

### 3. File Structure Check
When you look in the folder, do you see:
- [ ] Files directly in the folder (nzp.kvp, nzpconfig.json, etc. at same level)
- [ ] Files in a subfolder (like `nzp/nzp.kvp`)
- [ ] Files in multiple subfolders

### 4. Required Files Present?
Check that ALL of these are in the folder:
- [ ] `nzp.kvp`
- [ ] `nzpconfig.json`
- [ ] `nzpmetaconfig.json`
- [ ] `nzpports.json` (optional but recommended)
- [ ] `nzpupdates.json` (optional but recommended)
- [ ] `manifest.json` (should be at repository root if using Configuration Repository)

### 5. AMP Actions Taken?
- [ ] Clicked "Fetch Latest" in Configuration → Instance Deployment
- [ ] Refreshed browser page (F5 or Ctrl+R)
- [ ] Restarted AMP service completely
- [ ] Checked for any error messages in AMP logs

### 6. Template Discovery Check
When creating a new instance:
- [ ] Are OTHER templates showing up? (Like Minecraft, etc.)
- [ ] Is the list completely empty?
- [ ] Did you try searching for "nzp" in the interface?
- [ ] Did you scroll through the entire list?

### 7. File Permissions (Linux only)
If on Linux:
- [ ] Files are readable by AMP user
- [ ] AMP has access to the folder

## Most Common Issues

### Issue 1: Files in Wrong Location for Configuration Repository
**Fix:** For Configuration Repositories, files might need to be in:
```
templates/nzp/nzp.kvp
templates/nzp/nzpconfig.json
etc.
```

### Issue 2: Need to Restart AMP Service
**Fix:** A full service restart is often required (not just refresh in web interface)

### Issue 3: Files Not in DeploymentTemplates Folder
**Fix:** For Deployment Templates method, files MUST be in:
```
ADS/Plugins/ADSModule/DeploymentTemplates/
```
(Not in a subfolder, directly in this folder)

## Quick Fix to Try First

### Option A: Use Deployment Templates Method
1. Copy these 3 files to `ADS/Plugins/ADSModule/DeploymentTemplates/`:
   - nzp.kvp
   - nzpconfig.json
   - nzpmetaconfig.json
2. Files should be **directly** in that folder (no subfolders)
3. Restart AMP service
4. In web interface: Configuration → Instance Deployment → Fetch Latest
5. Refresh browser (F5)
6. Try creating instance

### Option B: Check Configuration Repository Structure
If using Configuration Repository, the repository might need files in a subfolder structure.

## Tell Me:
1. **Exact path where files are currently located**
2. **Which method you're using** (Configuration Repository or manual)
3. **Have you restarted the AMP service?**
4. **What do you see when creating a new instance?** (empty list? other templates? search results?)

