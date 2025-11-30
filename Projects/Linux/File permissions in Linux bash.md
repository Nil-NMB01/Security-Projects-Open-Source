# File Permissions in Linux

## Project Description

As part of my security learning journey, I worked on a task involving file and directory permissions in Linux. The goal was to understand how permissions work, how to analyze them, and how to update them to match different authorization requirements. To complete this activity, I walked through several steps that involved checking permissions, interpreting permission strings, and modifying them with the `chmod` command.

---

## Checking File and Directory Details

The first step was to examine the existing permissions for files and directories within the `projects` directory. I used the following command to display all files, including hidden ones, in detailed format:

```bash ls -la projects/ ```

The first line in the screenshot shows the command I entered, and the lines below it show the output. The output listed one directory named `drafts`, a hidden file named `.project_x.txt`, and five other project files. The first column in the output contains a 10-character string that represents the permissions set for each file or directory.

---

## Understanding the Permissions String

Each 10-character permissions string follows a consistent structure. Here is how it breaks down:

- **1st character:**
  Indicates the file type:

    * `d` → directory
    * `-` → regular file

- **2nd–4th characters:**
  Represent the **read (r)**, **write (w)**, and **execute (x)** permissions for the **user** (the owner).

- **5th–7th characters:**
  Indicate the read, write, and execute permissions for the **group**.

- **8th–10th characters:**
  Indicate the read, write, and execute permissions for **others** (anyone not the user or the group).

A hyphen (`-`) in any position means that the corresponding permission is **not** granted.

### Example

One of the files, `project_t.txt`, had the following permissions:

``` -rw-rw-r-- ```

This means:

- It is a **file** (`-`)
- **User**: read + write
- **Group**: read + write
- **Others**: read only
- No execute permissions are granted to anyone

---

## Changing File Permissions

Part of the task required me to modify permissions to meet certain security requirements. For example, I needed to remove write access from “others” for the file `project_k.txt`.

I used the following commands:

```bash chmod o-w project_k.txt ls -la ```

`chmod` updates the permissions on files and directories. The first argument specifies which permissions should be changed, and the second argument indicates the file or directory. After making the change, I used `ls -la` again to verify that the update was applied.

---

## Changing Permissions on a Hidden File

I also worked with a hidden file, `.project_x.txt`, which I identified as hidden because its name begins with a dot (`.`). The task required restricting write access for everyone, while ensuring that the user and the group still had read access.

I used the following commands:

```bash chmod u-w .project_x.txt chmod g-w .project_x.txt chmod g+r .project_x.txt ```

These commands:

- Removed write permissions from the **user** (`u-w`)
- Removed write permissions from the **group** (`g-w`)
- Added read permissions to the **group** (`g+r`)

---

## Changing Directory Permissions

Another part of the assignment required adjusting permissions for the `drafts` directory so only a specific user (`researcher2`) would have execute permissions. Execute permission is necessary to access or traverse a directory.

Since the group previously had execute access, I removed it with the following command:

```bash chmod g-x drafts/ ```

The user `researcher2` already had the correct permissions, so I did not need to add anything for them.

---

## Summary

Through this activity, I practiced analyzing and modifying file and directory permissions in Linux. I began by using `ls -la` to inspect existing permissions, then applied several `chmod` commands to update them. This exercise strengthened my understanding of permission structures, how they affect system security, and how to adjust them to meet specific requirements.

---
