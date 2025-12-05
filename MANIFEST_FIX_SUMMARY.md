# Manifest.json Fix Summary

## ✅ Issue Found and Fixed!

Your manifest.json was using the **wrong format**. AMP Configuration Repositories need a **repository-level manifest**, not a template definition format.

## What Changed

### ❌ Old Format (Wrong):
```json
{
  "Templates": [
    {
      "Name": "nzp",
      "DisplayName": "...",
      ...
    }
  ]
}
```

### ✅ New Format (Correct):
```json
{
  "id": "da848309-480a-4e9b-bec8-b7986f817733",
  "authors": ["l0cks-acab"],
  "origin": "https://github.com/l0cks-acab/nzp-amptemplate.git",
  "url": "https://github.com/l0cks-acab/nzp-amptemplate",
  "imagefile": "",
  "prefix": "",
  "repotype": "AppTemplates"
}
```

## Next Steps

Now that manifest.json is fixed, you may also need to check:

### 1. Template File Organization
AMP Configuration Repositories might expect templates in a subfolder structure. Check if files need to be in:
- `nzp/` subfolder, OR
- `templates/nzp/` subfolder

### 2. Commit and Push Changes
1. Commit the updated manifest.json
2. Push to GitHub
3. In AMP: Remove and re-add the Configuration Repository
4. Fetch Latest again

### 3. Verify Template Discovery
After pushing the fix:
1. Remove the repository from AMP Configuration Repositories
2. Re-add it: `l0cks-acab/nzp-amptemplate:main`
3. Click "Fetch Latest"
4. Restart AMP service
5. Try creating a new instance

## File Structure to Check

The template files might need to be organized as:
```
repository-root/
  manifest.json (✅ Now fixed!)
  nzp/
    nzp.kvp
    nzpconfig.json
    nzpmetaconfig.json
    nzpports.json
    nzpupdates.json
  README.md
```

OR files might be fine at root - test after pushing the manifest fix!

