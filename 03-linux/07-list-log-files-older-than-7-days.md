## Question  
How do you find and list the log files older than 7 days in the `/var/log` folder?

### 📝 Short Explanation  
This question tests your comfort with Linux file management and log housekeeping — a common task for DevOps and sysadmins.

## ✅ Answer  
You can use the `find` command with the `-mtime` option to locate files older than 7 days:

```bash
find /var/log -type f -mtime +7
find /var/log -type f -mtime +7 -name *.log
find /var/log -type f -mtime +7 -name *.log -exec ls -ltr {} \;
```

### 📘 Detailed Explanation  

#### 🔍 Breakdown of the command:

- `find`: The Linux command to search for files in a directory hierarchy.
- `/var/log`: The target directory that contains log files.
- `-type f`: Limits the search to files (not directories).
- `-mtime +7`: Filters files **modified more than 7 days ago**. -mtime stands for modification time
  - `+7` means strictly older than 7 days.
  - `-7` would mean newer than 7 days.

---
| Command                   | Explanation                                                    |
| ------------------------- | -------------------------------------------------------------- |
| `find /var/log -mtime +7` | Find files modified **more than 7 days ago** (Day 8, 9, 10...) |
| `find /var/log -mtime -7` | Find files modified **in the last 7 days** (Day 1 to Day 7)    |
| `find /var/log -mtime 7`  | Find files modified **exactly 7 days ago**                     |

#### 🛠️ Practical Usage:
If you want to **view the size and timestamp** of those files:
```bash
find /var/log -type f -mtime +7 -exec ls -lh {} \;
```

If you want to **delete** those files:
```bash
sudo find /var/log -type f -mtime +7 -delete
```
⚠️ Be careful with deletion — make sure you’ve reviewed the list first.

---

> Summary:  
> Use `find /var/log -type f -mtime +7` to list log files older than 7 days — a must-know for log maintenance in production servers.

---
