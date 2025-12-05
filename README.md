# NZP (Nazi Zombies Portable) AMP Template

An AMP (Application Management Panel) template for hosting Nazi Zombies Portable (NZP) dedicated servers.

## About NZP

Nazi Zombies Portable (NZP) is a Quake-based first-person shooter game featuring zombie survival gameplay. This template allows you to easily deploy and manage NZP dedicated servers using AMP.

## Prerequisites

Before using this template, you need to obtain the following files:

1. **NZP-specific FTEQW Binary**
   - Download `nzportable` (32-bit) or `nzportable64` (64-bit) for your platform
   - Place the executable in your AMP instance root directory

2. **Game Assets**
   - Download `pc-nzp-assets.zip`
   - Extract it alongside the binary (should create an `nzp` folder)

3. **QuakeC Files**
   - Download `fte-nzp-qc.zip`
   - Download `standard-nzp-qc.zip`
   - Extract both into the `nzp` directory
   - You should see `.dat` files in the `nzp` folder after extraction

For detailed download links and setup instructions, visit the [NZP Server Setup Documentation](https://docs.nzp.gay/server/server-setup).

## Installation

1. Copy the template files to your AMP instance:
   - `nzp.kvp`
   - `nzpconfig.json`
   - `nzpmetaconfig.json`

2. Ensure your directory structure looks like this:
   ```
   AMP Instance Root/
   ├── nzportable (or nzportable64)
   ├── nzp/
   │   ├── *.dat files (from QuakeC archives)
   │   └── (other NZP assets)
   └── (template files)
   ```

3. In AMP, create a new Generic Module instance and select the NZP template.

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

## Additional Resources

- [NZP Official Documentation](https://docs.nzp.gay/)
- [NZP Server Setup Guide](https://docs.nzp.gay/server/server-setup)
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

