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

## Default Ports

The template defines two ports that AMP will manage:

- **UDP Port 27500**: Main game port (configurable)
- **TCP Port 27501**: WebSocket port for web clients (configurable)

Make sure these ports are open in your firewall if you want the server to be accessible from the internet.

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


