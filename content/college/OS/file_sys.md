# file
- It is recorded on secondary storage such as magnetic disks, magnetic tapes and optical disks.
- a file is a sequence of bits, bytes, lines or records whose meaning is defined by the files creator and user.
- Contiguous logical address space
- Types:
    1. Data
    2. numeric
    3. character
    4. binary
    5. Program
- Contents defined by file’s creator
    1. text file,
    2. source file,
    3. executable file
## Attributes
1. Name – only information kept in human-readable form
2. Identifier – Along with the name, Each File has its own extension which identifies the type of the file.
3. Type – needed for systems that support different types
4. Location – pointer to file location on device
5. Size – current file size
6. Protection – controls who can do reading, writing, executing
7. Time, date, and user identification – data for protection, security, and usage monitoring
8. Information about files are kept in the directory structure, which is maintained on the disk

## Operation
1. Create
2. Write – at write pointer location
3. Read – at read pointer location
4. Reposition within file - seek
5. Delete
6. Truncate
7. Open(Fi) – search the directory structure on disk for entry Fi, and move the content of entry to memory
8. Close (Fi) – move the content of entry Fi in memory to directory structure on disk
- File is an abstract data type
# Access Method
## Sequencial access file
- A sequential access is that in which the records are accessed in some sequence
- the information in the file is processed in order, one record after the other.
- This access method is the most primitive one.
- Example: Compilers usually access files in this fashion.
## Ranodm access/ Direct
- Random access file organization provides, accessing the records directly.
- Each record has its own address on the file with by the help of which it can be directly accessed for reading or writing.
- The records need not be in any sequence within the file and they need not be in adjacent locations on the storage medium.
- The Direct Access is mostly required in the case of database systems
## Indexed sequencial access
- This mechanism is built up on base of sequential access.
- An index is created for each file which contains pointers to various blocks.
- Index is searched sequentially and its pointer is used to access the file directly.

# Directoy Oraganization
- operations on directory
    - Search for a file
    - Create a file
    - Delete a file
    - List a directory
    - Rename a file system
- to obatain
    - Efficiency – locating a file quickly
    - Naming – convenient to users
- Two users can have same name for different files
- The same file can have several different names
- Grouping – logical grouping of files by properties, (e.g., all Java programs, all games, …)
## Structure
- A collection of nodes containing information about all files
- Both the directory structure and the files reside on disk
## Single Level Directory
- A single directory for all users
- implementation is very simple.
- If the sizes of the files are very small then the searching becomes faster.
- File creation, searching, deletion is very simple since we have only one directory.
### disadvantages
- We cannot have two files with the same name.
- The directory may be very big therefore searching for a file may take so much time.
- Protection cannot be implemented for multiple users.
- There are no ways to group same kind of files.
## Two-Level
- Separate directory for each user
- Path name
- Can have the same file name for different user
- Efficient searching
- No grouping capability
## Tree structure
- In Tree structured directory system, any directory entry can either be a file or sub directory.
- Tree structured directory system overcomes the drawbacks of two level directory system.
- The similar kind of files can now be grouped in one directory.
## Acyclic
- two or more directory entry can point to the same file or sub directory.






