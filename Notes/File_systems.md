File Systems
============

- sequential access
- random access

Need a system to denote each sector on the disk platter
- How? -- the job of the file system

Allocation strategies
- allocate file like continuous memory allocation (base & limit)
  - user specifies length, file system allocates space all at one

Pros:
  - low storage overhead, only keeps track of two numbers
  - fast sequential access since data stored in continuous blocks
  - good to be used in Read-only files. CD_ROM for example
Cons:
  - hard to grow the file since a fixed chunk of sectors on the disk
  - large external fragmentation

Extent-based allocation
- same idea, except now multiple contiguous regions per file, so more flexibility

Linked allocation
- all blocks of file on linked list
- Pros
  - No external fragmentation
  - Files can be easily grown with no limit
  - Also easy to implement, though awkward to sparse space for disk pointer per blocks

- cons
  - large storage overhead
  - Potentially slow sequential access
  - difficult to compute random addresses

- in 32 bits Linux system, a block size is about 4k
- FAT is initially written somewhere on the disk and gets mounted with OS and thereby loaded to memory and FAT based files do memory accesses to the FAT.
  - A problem, with 4 TB drive, the table can be very big.
  - With FAT and the notion of cluster, the blocks are becoming bigger, thus small files may waste spaces in a block

Index allocation

Multi-level indexed files
- All the indirect and direct blocks are the full blocks.
- A number of inode is already allocated, restricting the number of files a system can have  
- using "touch" will just allocate an inode for the created file but not any blocks since the file size is 0

__Free Space Management__

Berkeley Fast File System (FFS) layout
- Partitions: like installing multiple OS on one disk drive
- super block: know the size of the partition, has
  1. inode map
  2. block bitmap
  3. inodes
  4. data blocks
