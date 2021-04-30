# Quantum Teleportation

Contrary to the name, quantum teleportation doesn't actually teleport a qubit physically, but instead teleports the information. Regardless of the distance between the qubits, the information will be reflected on the other qubit instantly, and without any medium required in between (thanks to entanglement).

Of course, this means that the required number of qubits already be present at the receiving end. Copying in the manner classical bits do is not possible, since that would measure the quantum state, effectively destroying the quantum state we're trying to copy.

suppose Alice wants to send a qubit to bob who is far away. before they move away they had entangled their qubits and now each has on of it. Now second qubit in our system is one of the entangled qubit that alice has. while the third qubit is second of the entangled qubit that bob has. While firsr qubit is the information we want to transfer to bob without knowing what it is.  

Here we will try to get make a qubit 1 in state |1> (information), and transfer it to qubit 3 which is far away. 
 
Since qubits start out in the `|0>` state, we'll use X gate to convert `q0` to  `|1>`.

Now, we try to entangle qubit 2 and 3 as required. Since quantum teleportation requires that the qubits be entangled, we'll entangle `q1` and `q2`. To achive the entanglement form of $\frac{1}{2^{1/2}} (|00> + |11>)$ we will use CNot gate.

Till now the final circuit would look like,

$\frac{1}{2^{1/2}} (|1> |00> + |1> |11>)$

Now, According to the quantum teleportation protocol, we'll need to apply a controlled-NOT and Hadamard gate to `q0` and `q1`. as a part of the algorythm. so the math would like below,

$\frac{1}{2^{1/2}} (|110> + |101>)$   after CNot gate

$\frac{1}{2} ((|0> - |1>) |10> + (|0> - |1>) |01>)$  after H gate on `q0`

$\frac{1}{2} (|01> |0> - |11> |0> + |00> |1> - |10> |1>)$  Rearragement

At this point, we will get four outcomes from the measurement of the first two qubits which are,

{ $ |01> |0> , |11> |0> , |00> |1> , |10> |1> $ }. 

from the above set we can say that, first part tells us the outcome of the firsr two qubits while last part tells us the outcome of the third qubit. As we know the information is $|1>$, so last two sets gives the right answer while firsr two does not. also we can say that all four answer has equal probability. So to get the correct answer will 100% we will use cnot gate on two and three after the measurement. that will flip the qubit 3 in firsr two case. which is what we want. and that will give us the right answer with full certainty.

