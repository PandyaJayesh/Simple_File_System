# Simple File System (SFS)

The **Simple File System (SFS)** is a minimalistic file system implemented in C. It supports basic file and directory operations, including file creation, deletion, display, directory navigation, and metadata management. The project demonstrates fundamental file system concepts such as inodes, block allocation, and bitmap-based space management.

---

## Key Features

- **Directory Operations**: 
  - `md <dir_name>`: Create a new directory.
  - `rd`: Reset to the root directory.
  - `ls`: List all files and directories in the current directory.
  - `cd <dir_name>`: Change to the specified directory.

- **File Operations**:
  - `create <file_name>`: Create a new file and input content (up to 3 blocks).
  - `display <file_name>`: Display the content of the specified file.
  - `rm <file_name>`: Remove the specified file or directory (recursively for directories).

- **System Metadata**:
  - `stats`: Display the number of free blocks and inode entries.
  - Mounting and managing the disk file `sfs.disk` with block size of 1024 bytes.

---

## Technical Highlights

### 1. **Data Structures**
- **Inode Table**: Stores information about files and directories. Each inode tracks up to three blocks.
- **Block Bitmap**: Tracks allocation of disk blocks.
- **Inode Bitmap**: Tracks allocation of inodes.
- **Directory Entries**: Store file and directory names along with associated inode indices.

### 2. **File System Operations**
- **Mounting**:
  - Reads metadata (bitmaps, inode table) from the disk file (`sfs.disk`) into memory.
- **Block and Inode Management**:
  - Uses bitmaps to track free/used disk blocks and inodes.
  - Allocates or frees resources dynamically during operations.
- **Recursive Deletion**:
  - Implements recursive directory deletion to free all associated resources.

### 3. **Command-line Interface**
- Provides a user-friendly prompt (`SFS::<current_directory>#`) for executing commands interactively.

---

## Sample Commands

1. **Mounting the File System**
   - Automatically mounts the file system when the program starts.
   
2. **Creating a Directory**
   ```bash
   md documents
3. **Navigating Directories**

    ```bash
    cd documents
4. **Creating a File**

    ```bash
    create file1.txt
* Input content for the file (up to 3 blocks). End input by pressing Esc.
5. **Displaying File Content**

    ```bash
    display file1.txt
6. **Listing Directory Contents**

    ```bash
    ls
7. **Removing a File**

    ```bash
    rm file1.txt
8. **Checking Disk Status**

    ```bash
    stats

## Implementation Details
### Block Management
* Disk blocks are allocated dynamically using a bitmap.
* Blocks are initialized with zeroes when allocated.
### Inode Table
* Supports up to 128 entries, each of which can track:
    * File or directory type.
    * Up to three disk blocks.
### File Content Storage
* File content spans across up to three blocks (if necessary).
* Implements mechanisms to read/write content block-by-block.
### Directory Structure
* Each directory can have up to 12 entries (stored across 3 blocks, with 4 entries per block).
## **Execution Steps**
1. Compile the Code:

    ```bash
    gcc sfs.c -o sfs
2. Run the Program:

    ```bash
    ./sfs
3. Execute Commands using the CLI as shown in the [Sample Commands]() section.

## Challenges and Learnings
* Understanding and implementing the inode-block model for file and directory management.
* Designing recursive algorithms for directory deletion.
* Optimizing bitmap-based resource allocation for efficient space management.
* Handling edge cases like full disk or inode table during operations.


## Credits

* **Guided by**: Prof. Anish Mathuria, DA-IICT
* **Developer**: Jayesh Pandya
* **Contact**: pandyajayesh7848@gmail.com


Feel free to modify the content or let me know if you'd like to add more details!
