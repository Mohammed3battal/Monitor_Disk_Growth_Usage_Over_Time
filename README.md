## Script: Monitor and Log Disk Usage Over Time in SQL Server

**Description**:
This script sets up a system to track and log disk space usage on each drive letter from within SQL Server. It collects both total and free space and logs it at each execution, allowing historical trend analysis for capacity planning and alerts.

**Steps Performed**:
1. Creates a database `DiskGrowthDB`.
2. Creates a logging table `DiskGrowthLog`.
3. Defines a stored procedure `LogDiskGrowth` that:
   - Uses `xp_fixeddrives` to get free space.
   - Uses `sys.master_files` to estimate total space per drive.
   - Logs the result in `DiskGrowthLog`.
4. Includes ready-to-use T-SQL reports:
   - View all logs
   - Disk usage by drive
   - Growth over time for a specific drive
   - Growth rate between each log entry
5. Can be scheduled via **SQL Server Agent** to log disk space regularly.

**Notes**:
- You must have permission to run `xp_fixeddrives`.
- Make sure SQL Server Agent is enabled to automate the log collection.
- This script stores data in MB; you can convert it to GB for reporting if needed.

**Requirements**:
- SQL Server 2008 or later
- `sysadmin` permission (for `xp_fixeddrives`)
- SQL Server Agent (for scheduling)
