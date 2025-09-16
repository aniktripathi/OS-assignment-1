# OS-assignment-1
Task 1: Process Creation Utility
========================================================
Python Code:
------------
def create_child_processes(n):
    processes = []
    for i in range(n):
        pid = os.fork()
        if pid == 0:  # Child process
            print(f"[Child {i+1}] PID={os.getpid()}, PPID={os.getppid()}, Message=Hello from child {i+1}")
            os._exit(0)
        else:
            processes.append(pid)
    for pid in processes:
        os.waitpid(pid, 0)
