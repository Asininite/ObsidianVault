Disk Scheduling Algorithms.  
  
1) FCFS - Requests are addressed in the order they arrive.  
  
2) SSTF- just like shortest job first, the request with shortest seek time (time required to locate data) are executed first. Seek time of requests is calculated and accordingly scheduled.  
  
3) SCAN- disk arm will move in a particular direction and addresses requests in its path after reaching the end of the disk, it reverses it's direction and repeats the previous process also known as elevator algorithm.  
  
4) LOOK- similar to scan except for disk arm in spite reaching end of the disk goes to the last request to be addressed in the front of the head and then reverses its direction. It prevents extra delay due to unnecessary traversal to disk end.