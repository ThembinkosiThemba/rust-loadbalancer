# Rust Loadbalancer

This Rust code demonstrates a simple load balancer implementation using threads and mutexes for synchronization. Let me walk you through it:

**LoadBalancer Struct:** This struct represents the load balancer. It contains a vector of server addresses (servers) and a Mutex to synchronize access to the current_index.

**Implementation of LoadBalancer:**
new function initializes a new LoadBalancer instance with the provided list of server addresses and initializes the current_index to 0.
next_server function retrieves the next server address from the list in a round-robin fashion. It locks the current_index mutex to ensure exclusive access to the index, increments the index, and returns the corresponding server address.

**Main Function:**
It creates a vector of server addresses (servers).
Then, it creates an Arc (atomic reference counting) pointer to a LoadBalancer instance, enabling it to be safely shared across threads.
A loop spawns multiple threads. Each thread will simulate sending 10 requests to the load balancer.
Inside each thread, it repeatedly calls next_server method on the load_balancer instance and prints the server address where the request is sent.
thread::sleep is called to ensure that all threads have sufficient time to execute before the program exits.