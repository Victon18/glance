# Disk scheduling
- For I/O, it requests the Operating system to access the disk.
- It is the technique that operating system uses to determine the request which is to be satisfied next.
- The main purpose is to select a disk request from the queue of IO requests and decide the schedule when this request will be processed.
- It ensures
    - Fairness
    - High throughout
    - Minimal traveling head time

## Seek Time
- It is the time taken in locating the disk arm to a specified track where the read/write request will be satisfied.
## Rotational Latency
- It is the time taken by the desired sector to rotate itself to the position from where it can access the R/W heads.
## Transfer Time
- It is the time taken to transfer the data.
## Disk Access Time
- Disk Access Time = Rotational Latency + Seek Time + Transfer Time
## Disk Response Time
- It is the average of time spent by each request waiting for the IO operation.

# Classic Algorithms
## First Come First Serve (FCFS)
- Handle I/O requests sequentially.
- Fair to all processes.
- Approaches random scheduling in performance if there are many processes/requests.
- Suffers from global zigzag effect.
## Shortest Seek Time First (SSTF)
- aSelects the request with the minimum seek time from the current head position.
- Also called Shortest Seek Distance First (SSDF) – It’s easier to compute distances.
- It’s biased in favor of the middle cylinders requests.
- SSTF scheduling is a form of SJF scheduling; may cause starvation of some requests.
# Elevators Algorithm
- Algorithms based on the common elevator principle.
- Four combinations of Elevator algorithms:
    - Service in both directions or in only one direction.
    - Go until last cylinder or until last I/O request.
## Scan
- The disk arm starts at one end of the disk, and moves toward the other end,
- servicing requests until it gets to the other end of the disk,
- where the head movement is reversed and servicing continues.
- It moves in both directions until both ends.
- Tends to stay more at the ends so more fair to the extreme cylinder requests.
## C-Scan
- The head moves from one end of the disk to the other, servicing requests as it goes.
- When it reaches the other end, however, it immediately returns to the beginning of the disk, without servicing any requests on the return trip.
- Treats the cylinders as a circular list that wraps around from the last cylinder to the first one.
- Provides a more uniform wait time than SCAN; it treats all cylinders in the same manner.
## Look
- The disk arm starts at the first I/O request on the disk, and moves toward the last I/O request on the other end,
- servicing requests until it gets to the other extreme I/O request on the disk,
- where the head movement is reversed and servicing continues.
- It moves in both directions until both last I/O requests;
## C-Look
- Arm only goes as far as the last request in each direction,
- then reverses direction immediately, without first going all the way to the end of the disk.
- In general, Circular versions are more fair but pay with a larger total seek time.
- Scan versions have a larger total seek time than the corresponding Look versions.

