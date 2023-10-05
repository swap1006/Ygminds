# Ygminds
Copy code
#!/bin/bash

# Database credentials
db_user="your_db_user"
db_password="your_db_password"
db_name="your_db_name"

# Backup directory
backup_dir="/path/to/backup/directory"

# Maximum number of backup copies to retain
max_backups=5

# Timestamp for the backup filename
timestamp=$(date +'%Y%m%d%H%M%S')

# Create a backup file with a timestamp
backup_filename="${db_name}_${timestamp}.sql"

# Perform the database backup
mysqldump -u "$db_user" -p"$db_password" "$db_name" > "$backup_dir/$backup_filename"

# Check if the backup was successful
if [ $? -eq 0 ]; then
    echo "Database backup completed: $backup_filename"
else
    echo "Database backup failed."
    exit 1
fi

# Remove old backup copies exceeding the maximum number
backup_files=("$backup_dir"/*)
if [ ${#backup_files[@]} -gt $max_backups ]; then
    num_to_delete=$(( ${#backup_files[@]} - max_backups ))
    for ((i = 0; i < num_to_delete; i++)); do
        old_backup="${backup_files[i]}"
        rm "$old_backup"
        echo "Deleted old backup: $old_backup"
