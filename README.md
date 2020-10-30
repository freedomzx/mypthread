# mypthread
An API that simulates the behaviors done by the pthread library.  

### int mypthread_create(mypthread_t* thread, pthread_attr_t* attr, void*(*function)(void*), void* arg)

Creates a new thread, stored in the address pointed to by thread, stores an attribute given by attr, and is employed on a function pointer with the given argument in arg.

### int mypthread_yield();

Commands a thread to yield, allowing other threads access to CPU memory.

### void mypthread_exit(void *value_ptr);

Terminates a thread, then allows other functions to go on ahead.  If value pointer is not null, then the return value is stored there.

### int mypthread_join(mypthread_t thread, void **value_ptr);

Commands a thread to wait for the thread given in the first argument to terminate before continuing operations.  If the given thread doesn't exist, proceed as normal.
If value_ptr is not equal to null, then the return value of the joined thread is stored there.

### int mypthread_mutex_init(mypthread_mutex_t *mutex, const pthread_mutexattr_t* mutexattr);

Initializes a mutex, to be used for mutual exluvisity on data shared between threads.  It will be stored in the mutex argument, and any attributes from mutexattr will be passed into it.

### int mypthread_mutex_lock(mypthread_mutex_t *mutex);

Locks a mutex if it is not yet in use, forces threads to be stay in the run queue if the mutex is already locked.

### int mypthread_mutex_unlock(mypthread_mutex_t *mutex);

Unlocks a mutex and lets other threads know that they can use it, as well as being taken off the run queue's waitlist.

### int mypthread_mutex_destroy(mypthread_mutex_t *mutex);

Destroys a mutex and lets other threads know they can be scheduled for CPU access again.

### static void schedule();

Uses the SJF scheduling algorithm to choose which thread is the next in line for CPU access.

