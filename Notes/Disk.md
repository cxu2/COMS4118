Disk
====
- moving the head is the most expensive disk operations

#### Disk Scheduling
- FCFS
  - causing a lot of head movements which we don't want
- SSTF
  - not fair
- SCAN
  -make up and down passes across all cylinders
  - also not fair, the oldest requests also wait longest
- C-SCAN
  - provides a more uniform wait time than SCAN
  - the head moves from one end of the disk to the other, servicing request as it goes
