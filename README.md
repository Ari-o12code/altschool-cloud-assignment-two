# altschool-cloud-assignment-two

> 1. 
```
#!/bin/bash

# Set default number of entries
entries=8

# Check for optional -n argument
if [[ "$1" =~ ^-n ]]; then
  # Extract number of entries if provided
  entries=${1#?n}
  shift
fi

# Check if directory argument is provided
if [ $# -eq 0 ]; then
  echo "Error: No directory specified"
  exit 1
fi

# Get directory path
dir_path="$1"

# Use du to get disk usage, top entries by default
disk_usage=$(du -h -s "$dir_path" | head -n "$entries")

# Print disk usage
echo "$disk_usage"
```


>2. 
```
#!/bin/bash

# Check if two arguments are provided
if [ $# -ne 2 ]; then
  echo "Error: Usage: backup.sh <source_dir> <destination_dir>"
  exit 1
fi

# Get source and destination directories
source_dir="$1"
dest_dir="$2"

# Create timestamp for backup filename
timestamp=$(date +%Y-%m-%d_%H-%M-%S)

# Create destination directory if it doesn't exist
mkdir -p "$dest_dir"

# Create tar archive with timestamp
tar -czf "$dest_dir/$source_dir-$timestamp.tar.gz" "$source_dir"

echo "Backup created: $dest_dir/$source_dir-$timestamp.tar.gz"
```
