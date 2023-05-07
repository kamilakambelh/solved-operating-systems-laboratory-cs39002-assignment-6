Download Link: https://assignmentchef.com/product/solved-operating-systems-laboratory-cs39002-assignment-6
<br>
<strong>Assignment 6:Implement a Memory Resident File System</strong>

It is required to implement a memory-resident file system in a memory block. The disk will be simulated as a set of contiguous blocks in memory. The file system will have the following features:

<ul>

 <li>The file system has to be created on a dynamically allocated memory block (created using <strong>malloc()</strong> for example).</li>

 <li>The size of the file system and the block size will be taken as inputs during file system creation. Typical value can be: 64MB and 1KB respectively.</li>

 <li>The first block (Block-0) in the file system will contain the <strong><em>Super Block</em></strong>, and will contain relevant information about the file system.</li>

 <li>The <strong><em>Super Block </em></strong>will contain information about the file system, like disk block size, total size of the file system, volume name, and other relevant information (mentioned below).</li>

</ul>

The following two alternatives have to be implemented:

<h1>Alternative 1: (Linked List Implementation using FAT)</h1>

<ul>

 <li>The free blocks are maintained as a bit vector stored in the super block. The number of bits will be equal to the number of blocks in the file system. If the i-th bit is 0, then block i is free; else, it is occupied.</li>

 <li>The data blocks of a file are maintained using a system-wide File Allocation Table (FAT), which will be stored in Block-1.</li>

 <li>The directory is stored in a fixed block (with pointer in super block), and assume single-level directory. Each directory entry contains a number that is an index to FAT, and indicates the first block in the file. If the i-th entry of FAT contains j, this means block-j logically follows block-I in the file.</li>

 <li>The data blocks will be stored from Block-2 onwards.</li>

</ul>

<h1>Alternative 2: (Indexed implementation using i-node)</h1>

<ul>

 <li>The free blocks are maintained as a linked list of the blocks. The superblock will contain a pointer to the first free block. The last free block will contain -1 in the pointer field.</li>

 <li>The data blocks of a file are maintained using index nodes or i-nodes. Each i-node will contain information about the data blocks, and will include 5 direct pointers, 1 singly indirect pointer, and 1 doubly indirect pointer. Each pointer will be 32 bits in size, and will indicate a block number. It will also store a <strong><em>type</em></strong> field indicating whether the file is a regular file or a</li>

</ul>

directory, and <strong><em>file size</em></strong> in bytes. The i-nodes will be stored in Block-1 and Block-2, in increasing order of their numbers (i.e. i-node-0 first, followed by i-node-1, and so on).

<ul>

 <li>The content of a directory file will be as follows. It will contain an array of records, each of size 16 bytes. The first 14 bytes srores the file name, and the last 2 bytes stores the inode number. Each directory will have two special entries “.” and “..”, indicating the current directory and the parent directory, respectively. For a block size of 512 bytes, 32 directory entries can be stored in each block.</li>

</ul>

The following API’s need to be supported for both the alternatives in the form of user-invocable functions from a C / C++ program. Define the parameters of the API functions appropriately.

<ul>

 <li><strong>my_open</strong> open a file for reading/writing (create if not existing)</li>

 <li><strong>my_close </strong>close an already open file</li>

 <li><strong>my_read</strong> read data from an already open file</li>

 <li><strong>my_write</strong> write data into an already open file</li>

 <li><strong>my_mkdir</strong> create a new directory</li>

 <li><strong>my_chdir</strong> change the working directory</li>

 <li><strong>my_rmdir</strong> remove a directory along with all its contents</li>

 <li><strong>my_copy</strong> copy a file between Linux file system and your file system</li>

 <li><strong>my_cat</strong> display the contents of the specified file</li>

</ul>

<strong>Evaluation Guidelines:</strong>

While entering marks, the partwise break up should also be entered according to the marking guidelines given below. There is a separate component for individual assessment, based on how the student answers questions

<table width="381">

 <tbody>

  <tr>

   <td width="30"><strong>Sl</strong></td>

   <td width="298"><strong>Item</strong></td>

   <td width="53"><strong>Marks</strong></td>

  </tr>

  <tr>

   <td width="30">1</td>

   <td width="298">Representation of free blocks for FAT</td>

   <td width="53">5</td>

  </tr>

  <tr>

   <td width="30">2</td>

   <td width="298">APIs for FAT based allocation</td>

   <td width="53">36</td>

  </tr>

  <tr>

   <td width="30">3</td>

   <td width="298">Overall implementation for FAT allocation</td>

   <td width="53">4</td>

  </tr>

  <tr>

   <td width="30">4</td>

   <td width="298">Representation of free blocks for i-node</td>

   <td width="53">5</td>

  </tr>

  <tr>

   <td width="30">5</td>

   <td width="298">APIs for i-node based allocation</td>

   <td width="53">36</td>

  </tr>

  <tr>

   <td width="30">6</td>

   <td width="298">Overall implementation for I-node based allocation</td>

   <td width="53">4</td>

  </tr>

  <tr>

   <td width="30"> </td>

   <td width="298"><strong>Total</strong></td>

   <td width="53">90</td>

  </tr>

 </tbody>

</table>


