# Linux Commands: Variables

This project explores variables in Linux, their types, usage, and practical applications in scripting and system administration. It demonstrates how variables enhance automation, efficiency, and flexibility in Linux environments.

**1. Understanding Variables in Linux**

Variables in Linux store temporary or persistent values used by processes, scripts, and applications. There are two main types:
- **Environment Variables** (System-wide, predefined values)
- **User-defined Variables** (Custom values set by users in scripts)

Example:

```sh
MY_VAR="Hello, Linux!"
echo $MY_VAR
```


**2. Types of Variables**

**System Variables (Predefined by Linux)**

| Variable | Description              | 
|:-------- | -----------------------
| $USER    | Current logged-in user   | 
| $HOME    | User's home directory    | 
| $PATH    | Directories searched for executables                           | 
| $SHELL   | Default shell being used | 
| $PWD     | Current working directory| 


Example usage:

```sh
echo "User: $USER"
echo "Home directory: $HOME"
```

**User-Defined Variables (Custom by Users)**

Users can define custom variables in scripts:

```sh
PROJECT_DIR="/home/user/project"
echo "Project directory is $PROJECT_DIR"
```


**3. Setting & Using Variables**

**Temporary Variables (Session Only)**

Set a variable for the current session:

```sh
export MY_TEMP="Linux Scripting"
echo $MY_TEMP
```

Once the session ends, the variable disappears.

**Persistent Variables (Stored in Profile Files)**

To make a variable permanent, add it to `~/.bashrc` or `~/.bash_profile`:

```sh
export API_KEY="123456789"
```

Apply changes:

```sh
source ~/.bashrc
```


**4. Using Variables in Shell Scripts**

**Example: Backup Script Using Variables**

```sh
#!/bin/bash
BACKUP_DIR="/home/user/backup"
SOURCE_DIR="/home/user/documents"

echo "Backing up files from $SOURCE_DIR to $BACKUP_DIR"
cp -r "$SOURCE_DIR" "$BACKUP_DIR"

echo "Backup completed!"
```

- `$BACKUP_DIR` defines the backup location.
- `$SOURCE_DIR` specifies the files to be backed up.

**5. Command Substitution in Variables**

Command output can be stored in variables:

```sh
CURRENT_DATE=$(date +%Y-%m-%d)
echo "Today's date is $CURRENT_DATE"
```

Example: Logging system uptime

```sh
UPTIME=$(uptime -p)
echo "System Uptime: $UPTIME"
```


**6. Conditional Usage of Variables**

Check if a variable is set:

```sh
if [ -z "$MY_VAR" ]; then
  echo "Variable is empty!"
else
  echo "Variable contains: $MY_VAR"
fi
```

Set default values if a variable is not defined:

```sh
echo ${EDITOR:-"nano"}
```

If `$EDITOR` is undefined, "nano" will be used.

**7. Security Considerations & Best Practices**

✅ Use export only for essential variables.

✅ Avoid storing sensitive credentials directly in environment variables.

✅ Clear confidential variables:
unset API_KEY



**8. Conclusion**

✔ Variables are essential for automation in Linux.

✔ System & user-defined variables offer flexibility in configurations.

✔ Persistent variables ensure long-term settings remain unchanged.

✔ Proper security prevents unauthorized access to sensitive data.
