# SSH Configuration Manager

A collection of scripts to easily manage SSH connections from the command line.

**Current Version: 1.1.0**

## 📋 Description

This project includes two main scripts:

- **`ssh-config`**: SSH configuration manager to add, edit, list and comment connections
- **`ssh-connect`**: Interactive SSH connector with filters and visual selection

## 🚀 Features

### ssh-config
- ✅ Add new SSH configurations
- ✅ Edit existing configurations
- ✅ List all configurations
- ✅ Comment/uncomment configurations
- ✅ Edit configuration file directly
- ✅ Intuitive command line interface

### ssh-connect
- ✅ Interactive mode with colorful interface
- ✅ Filter connections by name
- ✅ Numeric server selection
- ✅ Connection details visualization
- ✅ Real-time search
- ✅ List-only mode
- ✅ Parallel connections with multiple terminal windows
- ✅ Tmux integration with split panes
- ✅ Command broadcasting to multiple servers
- ✅ Interactive multi-server mode

## 📦 Installation

### macOS

1. **Clone or download the scripts:**
```bash
# Option 1: Clone from Git
git clone https://github.com/augustose/ssh-config.git
cd ssh-config

# Option 2: Download directly
curl -O https://raw.githubusercontent.com/augustose/ssh-config/main/ssh-config
curl -O https://raw.githubusercontent.com/augustose/ssh-config/main/ssh-connect
```

2. **Make scripts executable:**
```bash
chmod +x ssh-config ssh-connect
```

3. **Install in PATH (optional):**
```bash
# Option A: Move to /usr/local/bin (recommended)
sudo cp ssh-config ssh-connect /usr/local/bin/

# Option B: Create symbolic links
sudo ln -s $(pwd)/ssh-config /usr/local/bin/ssh-config
sudo ln -s $(pwd)/ssh-connect /usr/local/bin/ssh-connect

# Option C: Add to user PATH
echo 'export PATH="$HOME/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

### Linux

1. **Download the scripts:**
```bash
# Option 1: Clone from Git
git clone https://github.com/augustose/ssh-config.git
cd ssh-config

# Option 2: Download directly
wget https://raw.githubusercontent.com/augustose/ssh-config/main/ssh-config
wget https://raw.githubusercontent.com/augustose/ssh-config/main/ssh-connect
```

2. **Make scripts executable:**
```bash
chmod +x ssh-config ssh-connect
```

3. **Install in PATH:**
```bash
# Option A: Move to /usr/local/bin
sudo cp ssh-config ssh-connect /usr/local/bin/

# Option B: Create symbolic links
sudo ln -s $(pwd)/ssh-config /usr/local/bin/ssh-config
sudo ln -s $(pwd)/ssh-connect /usr/local/bin/ssh-connect

# Option C: Add to user PATH
echo 'export PATH="$HOME/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

## 📖 Usage

### ssh-config

#### Available commands:
```bash
ssh-config [OPTION]
```

#### Options:
- `add, -a, a` - Add new SSH configuration
- `comment, -c, c` - Comment existing configuration
- `list, -l, l` - List all configurations
- `edit, -e, e` - Edit configuration file with VI
- `update, -u, u` - Update existing configuration
- `version, -v, v` - Show version information
- `help, -h, h` - Show help

#### Examples:
```bash
# Add new configuration
ssh-config a

# List configurations
ssh-config l

# Comment configuration 'server'
ssh-config c server

# Edit configuration file
ssh-config e

# Update existing configuration
ssh-config u

# Show version
ssh-config v

# Show help
ssh-config h
```

### ssh-connect

#### Usage modes:
```bash
ssh-connect [OPTION] [SEARCH_TERM]
```

#### Options:
- `-h, --help, h` - Show help
- `-i, --interactive, i` - Interactive mode (default)
- `-l, --list, l` - List connections only
- `-f, --filter, f` - Apply filter to connection names
- `-v, --version, v` - Show version information

#### Parallel Connection Options:
- `--parallel <host1> <host2> ...` - Open multiple terminal windows
- `--parallel-tmux <host1> <host2> ...` - Use tmux with split panes
- `--broadcast <command> <host1> <host2> ...` - Run command on multiple servers
- `--multi, m` - Interactive multi-server mode

#### Examples:
```bash
# Interactive mode
ssh-connect

# List all connections
ssh-connect l

# Filter connections containing 'production'
ssh-connect production

# Apply specific filter
ssh-connect f staging

# Open 3 terminal windows
ssh-connect --parallel prod staging dev

# Use tmux with split panes
ssh-connect --parallel-tmux prod staging

# Run command on multiple servers
ssh-connect --broadcast 'uptime' prod staging

# Interactive multi-server mode
ssh-connect m

# Show version
ssh-connect v

# Show help
ssh-connect h
```

#### Interactive mode commands:
- `[number]` - Connect to selected server
- `f <term>` - Filter connections by term
- `c` - Clear filter
- `l` - List connections
- `h` - Show help
- `q` - Quit

#### Multi-Server Mode Commands:
- `[number]` - Toggle selection of server
- `a` - Select all servers
- `n` - Select none
- `s` - Start multi-server session
- `f <term>` - Filter connections by term
- `c` - Clear filter
- `h` - Show help
- `q` - Quit

## 🔧 Configuration

### SSH Configuration File

The scripts use the standard SSH configuration file located at:
- **macOS/Linux**: `~/.ssh/config`

If the file doesn't exist, it will be created automatically with correct permissions.

### Initial Setup

To get started quickly, you can use the included example file:

```bash
# Copy the example file
cp ssh-config.example ~/.ssh/config

# Edit with your real configurations
ssh-config -e
```

### Configuration File Structure

```bash
Host server-name
    HostName example.com
    User username
    Port 22
    IdentityFile ~/.ssh/id_rsa
    ForwardAgent yes
    ServerAliveInterval 60
```

## 🎨 Visual Features

### ssh-connect
- **Colorful interface** for better readability
- **Selection numbers** for connections
- **Configuration details** displayed with colors
- **Informative messages** with color codes

### Colors used:
- 🔵 **Blue**: Server names
- 🟢 **Green**: Selection numbers and success messages
- 🟡 **Yellow**: Warnings and active filters
- 🔴 **Red**: Errors
- 🟣 **Purple**: Configuration details
- 🔵 **Cyan**: Titles and headers

## 📝 Usage Examples

### Adding a new SSH connection
```bash
$ ssh-config -a
Adding new SSH configuration...
Host name (alias): my-server
Server address (hostname/IP): example.com
SSH user: admin
SSH port [22]: 2222
Use a specific key file? (y/n): y
Path to private key file: ~/.ssh/id_rsa
Add additional options? (y/n): y
Use ForwardAgent? (y/n): y
Use ServerAliveInterval? (y/n): y

Configuration added successfully.
You can now connect using: ssh my-server
```

### Connecting using ssh-connect
```bash
$ ssh-connect
SSH Connect - Interactive Mode
Type 'h' for help, 'q' to quit

Available SSH connections:
----------------------------------------
[ 1] prod-server          → example.com (admin) [key: id_rsa]
[ 2] staging-server       → staging.example.com (deploy) :2222 [key: staging_key]
[ 3] dev-server           → dev.example.com (developer) [key: dev_key]
[ 4] db-server            → db.example.com (dbadmin) [key: db_key]
[ 5] web-server           → web.example.com (webadmin) [key: web_key]

Commands:
  [number] - Connect to server
  f <term> - Filter connections
  c        - Clear filter
  l        - List connections
  h        - Show help
  q        - Quit

Enter command: 1
Connecting to prod-server...
Press Ctrl+C to cancel
```

## 🔒 Security

- Scripts respect SSH configuration file permissions
- File `~/.ssh/config` is created with `600` permissions (read-only for owner)
- Directory `~/.ssh` is created with `700` permissions if it doesn't exist
- No passwords or sensitive information are stored
- **Important**: Never share your real `~/.ssh/config` file as it may contain sensitive information

## 🔄 Version Management

### Automatic Version Updates

The project includes an automatic version management system:

- **Version tracking**: All scripts display current version with `-v` flag
- **Auto-increment**: Version automatically increments on each commit
- **Centralized versioning**: Single `VERSION` file controls all version numbers

### Manual Version Management

```bash
# Show current version
./update-version.sh show

# Increment patch version (1.1.0 → 1.1.1)
./update-version.sh patch

# Increment minor version (1.1.0 → 1.2.0)
./update-version.sh minor

# Increment major version (1.1.0 → 2.0.0)
./update-version.sh major

# Set specific version
./update-version.sh set 2.1.0
```

### Version Information

```bash
# Check ssh-config version
ssh-config -v

# Check ssh-connect version
ssh-connect -v
```

## 🐛 Troubleshooting

### Error: "Permission denied"
```bash
# Check configuration file permissions
ls -la ~/.ssh/config

# Fix permissions if necessary
chmod 600 ~/.ssh/config
chmod 700 ~/.ssh
```

### Error: "No SSH configurations defined"
- Verify that `~/.ssh/config` file exists
- Verify it contains valid configurations
- Use `ssh-config -a` to add the first configuration
- Use the example file: `cp ssh-config.example ~/.ssh/config`

### Error: "Command not found"
- Verify scripts are in PATH
- Verify they have execution permissions (`chmod +x`)
- Use absolute paths if necessary

## 📄 License

This project is licensed under the Apache License 2.0. See the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Augusto Sosa Escalada** - [augustose@gmail.com](mailto:augustose@gmail.com)

## 🤝 Contributing

Contributions are welcome. Please:

1. Fork the project
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📞 Support

If you encounter any issues or have questions:

- Open an issue on GitHub
- Contact the author: [augustose@gmail.com](mailto:augustose@gmail.com)

---

⭐ **If this project is useful to you, consider giving it a star on GitHub!** 