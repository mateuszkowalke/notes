# IPC

Inter Process Communication

### Shared files

This method uses parallel access to files to communicate between processes. In linux it uses flock API to synchronize access to the file. There can be only one writer at a time or many readers. It's achieved by 2 types of locks: exclusive (for writer) and shared (for readers).

### Shared memory

Linux systems provide two separate APIs for shared memory: the legacy System V API and the more recent POSIX one. These APIs should never be mixed in a single application, however. A downside of the POSIX approach is that features are still in development and dependent upon the installed kernel version, which impacts code portability. For example, the POSIX API, by default, implements shared memory as a memory-mapped file: for a shared memory segment, the system maintains a backing file with corresponding contents. Shared memory under POSIX can be configured without a backing file, but this may impact portability.ett