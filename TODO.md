# TODO - Pending Features

This document tracks pending features and enhancements for the SSH Configuration Manager project.

## 📋 Status Legend
- 🔴 **Not Started** - Feature not yet implemented
- 🟡 **In Progress** - Feature being developed
- 🟢 **Completed** - Feature implemented and tested
- ⭐ **High Priority** - Important features for next release

---

## 🔧 ssh-config Script Enhancements

### Configuration Management
- 🔴 **Delete/Remove configurations** - Currently only comments them out
  - Add `delete` or `remove` command option
  - Permanently remove host blocks from config file
  - Confirmation prompt before deletion
  - Option to backup before deletion

- 🔴 **Duplicate/Clone configurations** - Copy existing config with new name
  - Add `duplicate` or `clone` command option
  - Copy all settings from existing host to new host
  - Interactive prompt for new host name
  - Option to modify settings during cloning

- 🔴 **Import/Export configurations** - Backup/restore SSH configs
  - Export current config to JSON/YAML format
  - Import configs from external files
  - Merge configurations from different sources
  - Backup/restore functionality

### Validation & Testing
- 🔴 **Test connection** - Ping or test SSH connectivity before adding
  - Test SSH connectivity before saving configuration
  - Ping test for basic reachability
  - Validate SSH key authentication
  - Connection timeout testing

- 🔴 **Configuration validation** - Check syntax and required fields
  - Validate SSH config syntax
  - Check for required fields (Host, HostName, User)
  - Detect duplicate host names
  - Validate file paths for keys

### Search & Operations
- 🔴 **Search within configurations** - Find specific settings across all hosts
  - Search by IP address, username, or key file
  - Find hosts with specific SSH options
  - Search by port number or other parameters
  - Display search results with context

- 🔴 **Bulk operations** - Add multiple servers from a file
  - Import servers from CSV/JSON file
  - Batch add multiple configurations
  - Template-based server creation
  - Bulk update operations

### Key Management
- 🔴 **Key management** - Generate, list, or manage SSH keys
  - Generate new SSH key pairs
  - List existing SSH keys
  - Copy keys to remote servers
  - Key rotation and management
  - Key permissions validation

---

## 🔌 ssh-connect Script Enhancements

### Connection Features
- 🟢 **Parallel connections** - Connect to multiple servers at once ✅ **COMPLETED**
  - Multiple terminal windows
  - Tmux split panes
  - Command broadcasting
  - Interactive multi-server mode

- 🔴 **Quick connect by partial name** - `ssh-connect prod` to connect to prod-server
  - Fuzzy matching for host names
  - Auto-completion for partial matches
  - Priority for exact matches
  - Fallback to interactive selection

- 🔴 **Connection status** - Show if servers are reachable
  - Ping test for all servers
  - SSH connectivity check
  - Display online/offline status
  - Connection latency information

### History & Favorites
- 🔴 **Recent connections** - Show last 5-10 used connections
  - Track connection history
  - Display recent connections at top
  - Quick access to recently used servers
  - History persistence across sessions

- 🔴 **Connection history** - Track and display connection usage
  - Log connection timestamps
  - Connection duration tracking
  - Usage statistics and analytics
  - Export connection logs

- 🔴 **Favorites/Pinned servers** - Mark frequently used servers
  - Pin/unpin servers as favorites
  - Display favorites at top of list
  - Quick access to favorite servers
  - Favorites persistence

### Advanced Connection Options
- 🔴 **Connection timeout settings** - Custom timeout per server
  - Per-server timeout configuration
  - Global timeout settings
  - Connection retry logic
  - Timeout override for specific commands

- 🔴 **SSH options override** - Temporary SSH flags for connection
  - Override SSH options for single connection
  - Custom SSH flags and parameters
  - Temporary key file specification
  - Port override for specific connections

---

## 🛠️ General Improvements

### User Experience
- 🔴 **Configuration backup** - Auto-backup before changes
  - Automatic backup before modifications
  - Configurable backup retention
  - Restore from backup functionality
  - Backup compression and encryption

- 🔴 **Configuration diff** - Show what changed in config
  - Diff view for configuration changes
  - Highlight modifications
  - Revert specific changes
  - Change history tracking

### Organization & Management
- 🔴 **Server grouping** - Organize servers by environment/team
  - Group servers by environment (prod, staging, dev)
  - Team-based organization
  - Custom grouping and tagging
  - Group-based operations

- 🔴 **Connection statistics** - Usage analytics
  - Connection frequency analysis
  - Server usage patterns
  - Performance metrics
  - Usage reports and exports

### Integration & Automation
- 🔴 **Integration with SSH agents** - Key management integration
  - SSH agent integration
  - Key loading and management
  - Agent status checking
  - Automatic key addition

- 🔴 **API and automation** - Scriptable interface
  - JSON output for automation
  - API-like interface for scripts
  - Integration with CI/CD pipelines
  - Automated server management

---

## 🎯 Priority Matrix

### High Priority (Next Release)
1. Delete/Remove configurations
2. Quick connect by partial name
3. Test connection before adding
4. Configuration backup
5. Connection status check

### Medium Priority
1. Duplicate/Clone configurations
2. Recent connections
3. Favorites/Pinned servers
4. Configuration validation
5. Search within configurations

### Low Priority (Future Releases)
1. Import/Export configurations
2. Bulk operations
3. Key management
4. Connection history
5. Connection timeout settings
6. SSH options override
7. Server grouping
8. Connection statistics
9. Integration with SSH agents
10. API and automation

---

## 📝 Implementation Notes

### Technical Considerations
- Maintain backward compatibility
- Preserve existing functionality
- Add comprehensive error handling
- Include proper logging and debugging
- Ensure cross-platform compatibility

### Testing Requirements
- Unit tests for new functions
- Integration tests for workflows
- Cross-platform testing
- Performance testing for bulk operations
- User acceptance testing

### Documentation Updates
- Update README.md with new features
- Add usage examples
- Include troubleshooting guides
- Create migration guides for new features

---

## 🔄 Version Planning

### Version 2.0 (Next Major Release)
- Delete/Remove configurations
- Quick connect by partial name
- Test connection functionality
- Configuration backup
- Connection status check

### Version 2.1
- Duplicate/Clone configurations
- Recent connections
- Favorites/Pinned servers
- Configuration validation

### Version 2.2
- Search within configurations
- Import/Export configurations
- Connection history
- Connection timeout settings

### Version 3.0 (Future)
- Bulk operations
- Key management
- Server grouping
- Advanced analytics
- API and automation features 