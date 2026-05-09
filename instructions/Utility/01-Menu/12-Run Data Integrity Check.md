# Run Data Integrity Check
**Run Data Integrity Check Now**

## When to Use
- When you want to check if your project data has any anomalies
- When you want to detect and repair invisible issues like tree structure inconsistencies or duplicate IDs
- When you want to verify data health after importing data or making bulk edits

## What It Does
Automatically scans the entire project and detects data inconsistencies. Detected issues are displayed in a list, and selected issues can be auto-repaired.

Main issues detected:
- Duplicate IDs
- File/folder naming rule violations
- Tree structure inconsistencies (circular references, orphaned nodes, etc.)
- Tag reference inconsistencies
- Data type errors

## How to Use
1. Select Utility > **Run Data Integrity Check Now**
2. The scan runs and results are displayed in a dialog
3. If issues are found, review them in the list
4. Check the items you want to repair
5. Click **Repair Selected** to execute repairs

## Dialog Operations

### Result List
Each item displays the following information:
- **Severity icon**: ❌ Error (red) / ⚠️ Warning (yellow) / ℹ️ Info (blue)
- **Issue description**: Specific details
- **Location**: Target category name or chunk name
- **Repair info**: If auto-repair is possible, repair details are shown in green

### Filters
- **Severity**: Filter by severity (All / Errors / Warnings / Info)
- **Category**: Filter by validator type
- **Only repairable**: Show only repairable issues

### Executing Repairs
1. Check the items you want to repair (**Select All** for bulk selection)
2. Click **Repair Selected (N)**
3. Click **Confirm & Repair** in the confirmation dialog
4. After repair, a re-validation automatically runs and results are updated

## Notes
- If no issues are found, "No issues found" is displayed
- After repair, the project is automatically saved
- Scanning alone makes no changes (safe until you execute repairs)

## Related

- [Path Repair](13-Path%20Repair.md)
- [Project](../../File/01-Basics/01-File%20Menu%20Basics.md)
- [BackUp](../../File/02-Menu/09-BackUp/README.md)
