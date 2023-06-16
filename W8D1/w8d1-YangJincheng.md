## OSNotes-W8D1

#### Overview

Security

+ Definition

+ Example: login, password

#### Lecture Notes

**Security vs. Safety**

Safety is generally thought of in terms of data integrity. Backups, checksums, etc all ensure that the data is safe from failure.

Security is protecting data from unauthorized access, such as private info being viewed by a trojan, or database tables being dropped from SQL injection.

**Goals & Threats of Security**

![](https://s3.bmp.ovh/imgs/2023/06/16/118078755b16d583.png)

**Authentication & AcessControl**

authentication: login

access control: password

**Denial of Service (DoS)**

a denial-of-service attack (DoS attack) is a cyber-attack in which the perpetrator seeks to make a machine or network resource unavailable to its intended users by temporarily or indefinitely disrupting services of a host connected to a network.

**Trusted Computing Base (TCB)**

The trusted computing base (TCB) of a computer system is the set of all hardware, firmware, and/or software components that are critical to its security, in the sense that bugs or vulnerabilities occurring inside the TCB might jeopardize the security properties of the entire system. 

A key part of TCS is **Access Monitor**.

<img src="https://s3.bmp.ovh/imgs/2023/06/16/421c37978ad1743a.png" title="" alt="" width="427">

**Protection Domain**

Protection domains let you define security or user-defined policies for different network segments monitored by a single appliance.

A **domain** refers to a logical boundary within which a set of resources are managed and accessed.

**Rights**, on the other hand, refer to permissions granted to users or processes within a domain.

![](https://s3.bmp.ovh/imgs/2023/06/16/f6c73aa7bd13add6.png)

In Unix, the domains of a process are determined by its UID and GID. 

**Access Control List (ACL)**

An access control list (ACL) is a list of rules that specifies which users or systems are granted or denied access to a particular object or system resource. 

<img src="https://s3.bmp.ovh/imgs/2023/06/16/a314520ff2ea94c9.png" title="" alt="" width="373">

**Bell-LaPadula Model (BLP)**

The Bell–LaPadula model focuses on data confidentiality and controlled access to classified information.

The Bell–LaPadula model is built on the concept of a state machine with a set of allowable states in a computer system. The transition from one state to another state is defined by transition functions.

The model defines one discretionary access control (DAC) rule and two mandatory access control (MAC) rules with three security properties:

+ The **Simple Security Property** states that a subject at a given security level may not read an object at a higher security level.

+ The *** (Star) Security Property** states that a subject at a given security level may not write to any object at a lower security level.

+ The **Discretionary Security Property** uses an access matrix to specify the discretionary access control.

<img src="https://s3.bmp.ovh/imgs/2023/06/16/3af9b7702bc0def6.png" title="" alt="" width="374">

 **Biba Model**

The Biba model defines a set of security rules, the first two of which are similar to the Bell–LaPadula model. These first two rules are the reverse of the Bell–LaPadula rules:

+ The Simple Integrity Property states that a subject at a given level of integrity must not read data at a lower integrity level (no read down).

+ The * (star) Integrity Property states that a subject at a given level of integrity must not write to data at a higher level of integrity (no write up).

+ Invocation Property states that a process from below cannot request higher access; only with subjects at an equal or lower level.
