# NZP (Nazi Zombies Portable) AMP Template

An AMP (Application Management Panel) template for hosting Nazi Zombies Portable (NZP) dedicated servers.

## About NZP

Nazi Zombies Portable (NZP) is a Quake-based first-person shooter game featuring zombie survival gameplay. This template allows you to easily deploy and manage NZP dedicated servers using AMP.

## Prerequisites

Before using this template, you need to obtain the following files:

1. **NZP-specific FTEQW Binary**
   - Download from the [NZP GitHub Releases](https://github.com/nzp-team/nzportable/releases) page
   - For Windows: Download `nzportable-win64.zip` (64-bit) or `nzportable-win32.zip` (32-bit)
   - For Linux: Download `nzportable-linux64.zip` (64-bit) or `nzportable-linux32.zip` (32-bit)
   - Extract the archive and place the `nzportable` (or `nzportable64`) executable in your AMP instance root directory

2. **Game Assets**
   - Download `pc-nzp-assets.zip` from the [NZP GitHub Releases](https://github.com/nzp-team/nzportable/releases) page
   - If not available as a separate file, the assets may be included in the main game package
   - Extract it alongside the binary (should create an `nzp` folder)

3. **QuakeC Files**
   - Download `fte-nzp-qc.zip` from the [NZP GitHub Releases](https://github.com/nzp-team/nzportable/releases) page
   - Download `standard-nzp-qc.zip` from the [NZP GitHub Releases](https://github.com/nzp-team/nzportable/releases) page
   - Extract both into the `nzp` directory
   - You should see `.dat` files in the `nzp` folder after extraction
   
   **Note**: If these files are not available as separate downloads, they may be included in the main game release package. Check the release assets on GitHub for all available files.

For detailed download links and setup instructions, visit the [NZP Server Setup Documentation](https://docs.nzp.gay/server/server-setup).

## Installation

### Loading the Template into AMP

#### Method 1: Using AMP's Deployment Templates (Recommended)

1. **Locate your AMP installation directory** on your server
   - On Linux: Typically `/opt/amp` or `/home/amp`
   - On Windows: Typically `C:\Program Files\AMP` or your installation location
   - The path may also be shown in your AMP logs (e.g., `__VDS__ADS01`)

2. **Navigate to the Deployment Templates folder**:
   - Path: `ADS/Plugins/ADSModule/DeploymentTemplates/`
   - If using a configuration repository, it may be: `ADS/Plugins/ADSModule/DeploymentTemplates/CubeCoders-AMPTemplates/`
   - If the `DeploymentTemplates` directory doesn't exist, create it

3. **Place the template files** in the DeploymentTemplates directory:
   - Copy the following files directly into `DeploymentTemplates/`:
     - `nzp.kvp`
     - `nzpconfig.json`
     - `nzpmetaconfig.json`
   - **Important**: Files should be in the root of DeploymentTemplates, not in a subdirectory

4. **Refresh AMP to recognize the template**:
   - Log into the AMP web interface
   - Navigate to **Configuration** → **Instance Deployment**
   - Click **"Fetch Latest"** or **"Update Templates"** button
   - Refresh your browser page

5. **Create a new instance**:
   - In the AMP web interface, click **"Create Instance"** or **"Add Instance"**
   - **Important**: Templates appear as applications directly, not under "Generic Module"
   - Look for **"nzp"** or **"Nazi Zombies Portable"** in the application/module list
   - Select it and follow the instance creation wizard
   - The template will automatically use the Generic Module backend

#### Method 2: Using Configuration Repository (If Already Set Up)

If you've already added the repository as a configuration source (as shown in your logs):

1. The template should already be downloaded to: `Plugins/GenericModule/templates/nzp/`
2. Go to **Configuration** → **Instance Deployment** in AMP
3. Click **"Fetch Latest"** to refresh templates
4. Create a new instance and look for "nzp" or "Generic" module

#### Method 3: Manual Configuration

If the template still doesn't appear:

1. **Create a new Generic Module instance** manually:
   - In AMP, go to **Instances** → **Create New Instance**
   - If "Generic" isn't listed, you may need to enable it in AMP settings
   - Some AMP versions require enabling Generic Module in **Configuration** → **Modules**

2. **Manually configure** the instance using the template files:
   - After creating a Generic instance, go to its **Configuration** tab
   - Copy the contents of `nzp.kvp` into the instance's KVP/Startup settings
   - Configure settings from `nzpconfig.json` in the Settings section

### Setting Up the Server Files

After creating the instance, ensure your directory structure looks like this:

```
AMP Instance Root/
├── nzportable (or nzportable64)
├── nzp/
│   ├── *.dat files (from QuakeC archives)
│   └── (other NZP assets)
└── (template files - if using Method 2)
```

**Important**: The `nzportable` binary and `nzp` folder with assets must be in the instance root directory before starting the server.

## Configuration

The template provides the following configurable settings through AMP's interface:

- **Server Port (UDP)**: Main game port for UDP connections (default: 27500)
- **Server Port (TCP/WebSocket)**: WebSocket port for web client connections (default: 27501)
- **Protocol Name**: Server protocol identifier (default: "NZP-REBOOT")
  - Use "NZP-REBOOT" for desktop clients
  - Use "NZP-REBOOT-WEB" for web clients
- **Minimum Tick Rate**: Minimum server tick rate (default: 20)
- **Maximum Tick Rate**: Maximum server tick rate (default: 1000)
- **Public Server**: Whether the server should be publicly listed (default: true)
- **Server Hostname**: Display name for your server (default: "NZP Server")
- **Max Clients**: Maximum number of players (default: 32, max: 64)

## Usage

1. Configure your server settings in the AMP interface
2. Start the server instance
3. The server will launch with the `-dedicated` flag and your configured settings
4. Players can connect using the server's IP address and UDP port

## Server Management

- **Start**: Starts the NZP dedicated server
- **Stop**: Sends the `quit` command to gracefully shut down the server
- **Restart**: Stops and starts the server
- **Console**: Access the server console through AMP to run commands and view logs

## Ports

The template defines two ports that AMP will manage:

- **UDP Port 27500**: Main game port (configurable)
- **TCP Port 27501**: WebSocket port for web clients (configurable)

Make sure these ports are open in your firewall if you want the server to be accessible from the internet.

## Troubleshooting

### Server won't start
- Verify that the `nzportable` binary is in the root directory
- Check that the `nzp` folder exists with the required `.dat` files
- Review the AMP console for error messages

### Players can't connect
- Ensure the UDP port is open in your firewall
- Verify the server is set to public if you want it listed
- Check that the protocol name matches your client version

### Missing assets
- Re-download and extract `pc-nzp-assets.zip`
- Ensure QuakeC files (`fte-nzp-qc.zip` and `standard-nzp-qc.zip`) are extracted into the `nzp` directory

### Template not appearing in AMP
- Verify the template files are in the correct location: `AMP/instances/GenericModule/templates/nzp/`
- Ensure all three files are present: `nzp.kvp`, `nzpconfig.json`, `nzpmetaconfig.json`
- Restart the AMP service to refresh the template list
- Check file permissions to ensure AMP can read the template files

### Git/Configuration Repository Errors
If you encounter "fatal: not in a git directory" errors when adding the repository as a configuration source:
- The template files have already been downloaded and are ready to use
- You don't need to add it as a configuration repository - the template is already available
- Simply create a new Generic Module instance and select "nzp" from the template dropdown
- If you want automatic updates, ensure your GitHub repository is properly initialized with git and the files are committed

### Template Not Appearing When Creating Instance
**Important**: Generic Module is built-in to AMP and doesn't need to be enabled. Templates appear directly as applications, not under a "Generic Module" option.

If you don't see "nzp" or "Nazi Zombies Portable" when creating a new instance:

1. **Verify template location**:
   - Templates should be in: `ADS/Plugins/ADSModule/DeploymentTemplates/`
   - Files should be directly in this folder (not in a subdirectory)
   - Ensure files are named exactly: `nzp.kvp`, `nzpconfig.json`, `nzpmetaconfig.json`
   - Check file permissions - AMP needs read access to these files

2. **Refresh templates** (CRITICAL STEP):
   - Go to **Configuration** → **Instance Deployment** in AMP
   - Click **"Fetch Latest"** or **"Update Templates"** button
   - Wait for the process to complete (may take a minute)
   - **Refresh your browser page** (F5 or Ctrl+R)

3. **Check the application list**:
   - When creating a new instance, scroll through the entire list of applications
   - Look for **"nzp"** (lowercase) or **"Nazi Zombies Portable"** (full name)
   - Templates appear as applications, not under a "Generic" category
   - Try using the search/filter box if available

4. **Verify template files are valid**:
   - Check that `nzp.kvp` has proper formatting (no syntax errors)
   - Ensure `nzpconfig.json` is valid JSON (you can validate at jsonlint.com)
   - Check AMP logs for any errors about template loading

5. **Alternative locations to check**:
   - If using a configuration repository, templates may be in: `Plugins/GenericModule/templates/nzp/`
   - Some AMP versions use: `instances/GenericModule/templates/`
   - Check your AMP logs to see where it's looking for templates

6. **If still not working**:
   - Restart the AMP service completely
   - Check AMP version - older versions may have different template locations
   - Verify you have the latest template files from this repository

## Additional Resources

- [NZP Official Documentation](https://docs.nzp.gay/)
- [NZP Server Setup Guide](https://docs.nzp.gay/server/server-setup)
- [NZP GitHub Repository](https://github.com/nzp-team/nzportable) - Download binaries and source code
- [NZP GitHub Releases](https://github.com/nzp-team/nzportable/releases) - Download latest builds
- [AMP Generic Module Documentation](https://github.com/CubeCoders/AMP/wiki/Configuring-the-'Generic'-AMP-module)
- [AMP Templates Repository](https://github.com/CubeCoders/AMPTemplates)

## Contributing

If you find issues with this template or have suggestions for improvements, please submit a pull request or open an issue in the repository.

## License

This template is provided as-is for the AMP community. Refer to the AMPTemplates repository for licensing information.

## Notes

- This template uses command-line arguments to configure the server. Settings are passed directly to the NZP binary on startup.
- The template supports both Windows and Linux platforms.
- Make sure you have sufficient resources allocated (minimum 512MB RAM recommended, 1GB+ for better performance).

