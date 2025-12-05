# Solution Steps: Template Not Appearing

## Step-by-Step Fix

### Option 1: Use Deployment Templates Method (Recommended - Easiest)

1. **Find your AMP installation directory**
   - Windows: Usually `C:\Program Files\AMP` or similar
   - Linux: Usually `/opt/amp` or `/home/amp`

2. **Navigate to Deployment Templates folder**
   - Go to: `ADS/Plugins/ADSModule/DeploymentTemplates/`
   - Create this folder if it doesn't exist

3. **Copy these 3 files directly into that folder**:
   - `nzp.kvp`
   - `nzpconfig.json`
   - `nzpmetaconfig.json`
   - **Important:** Files go directly in the folder, NOT in a subfolder

4. **Restart AMP service completely**
   - Stop the service
   - Wait 10 seconds
   - Start the service again

5. **In AMP web interface:**
   - Go to **Configuration** → **Instance Deployment**
   - Click **"Fetch Latest"** or **"Update Templates"**
   - Wait for it to complete
   - **Refresh your browser** (F5 or Ctrl+R)

6. **Create a new instance:**
   - Click **"Create Instance"** or **"Add Instance"**
   - Look for **"nzp"** or **"Nazi Zombies Portable"** in the list
   - It should appear as an application option

### Option 2: Check Configuration Repository Structure

If you want to use Configuration Repository, the repository structure might need to change.

**Current structure might not be recognized. Try:**
1. Move template files to a `templates/nzp/` subfolder in your repository
2. Update manifest.json if needed
3. Commit and push changes
4. In AMP: Remove the repository and re-add it
5. Fetch latest again

## Critical Checklist

- [ ] Files are in the correct folder
- [ ] All required files are present (3 minimum)
- [ ] Files are directly in the folder (no subfolders for Deployment Templates)
- [ ] AMP service has been RESTARTED (not just refreshed)
- [ ] "Fetch Latest" has been clicked in web interface
- [ ] Browser page has been refreshed
- [ ] No filters are hiding templates
- [ ] File names match exactly (case-sensitive)

## Still Not Working?

If Option 1 doesn't work, tell me:
1. **Exact path** where you placed the files
2. **What you see** when creating a new instance (empty list? other templates? errors?)
3. **Any error messages** in AMP logs

