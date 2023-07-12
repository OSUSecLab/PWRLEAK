

## The emulation based interpolator to test the energy consumption of a instruction.



### Usage

Compile the kernel module. 

```shell
$ sudo depmod

$ sudo modprobe kvm

$ sudo modprobe kvm-amd
```

Measurement for evaluation

```shell
$ virsh start <domain-name>

$ dmesg -T | tail -100
```

Sample output

```
[Tue Jul 11 03:05:42 2023] emulate repeat times:5000000
[Tue Jul 11 03:05:42 2023] measure energy for empty loop
[Tue Jul 11 03:05:42 2023] Start measure for process 38923. CORENERGE_MSR: 0x1884abf6.
[Tue Jul 11 03:05:42 2023] End measure for process 38923. CORENERGY_MSR: 0x1884abf6.
[Tue Jul 11 03:05:42 2023] total energy consumption:0.
[Tue Jul 11 03:05:42 2023]  
[Tue Jul 11 03:05:42 2023] measure energy for loop+init: 'mov %eax, %ecx'
[Tue Jul 11 03:05:42 2023] Start measure for process 38923. CORENERGE_MSR: 0x1884abf6.
[Tue Jul 11 03:05:42 2023] End measure for process 38923. CORENERGY_MSR: 0x1884b4b2.
[Tue Jul 11 03:05:42 2023] total energy consumption:2236.
[Tue Jul 11 03:05:42 2023] measure energy for loop+init+emulate: 'mov %eax, %ecx'
[Tue Jul 11 03:05:42 2023] Start measure for process 38923. CORENERGE_MSR: 0x1884b4b2.
[Tue Jul 11 03:05:42 2023] End measure for process 38923. CORENERGY_MSR: 0x1884bdcc.
[Tue Jul 11 03:05:42 2023] total energy consumption:2330.
[Tue Jul 11 03:05:42 2023]      emulate 'mov %%eax, %%ecx'. energy consumption:94.
[Tue Jul 11 03:05:42 2023]  
[Tue Jul 11 03:05:42 2023] measure energy for loop+init: 'inc %ecx'
[Tue Jul 11 03:05:42 2023] Start measure for process 38923. CORENERGE_MSR: 0x1884bdcc.
[Tue Jul 11 03:05:42 2023] End measure for process 38923. CORENERGY_MSR: 0x1884c4a9.
[Tue Jul 11 03:05:42 2023] total energy consumption:1757.
[Tue Jul 11 03:05:42 2023] measure energy for loop+init+emulate: 'inc %ecx'
[Tue Jul 11 03:05:42 2023] Start measure for process 38923. CORENERGE_MSR: 0x1884c4a9.
[Tue Jul 11 03:05:42 2023] End measure for process 38923. CORENERGY_MSR: 0x1884cbc2.
[Tue Jul 11 03:05:42 2023] total energy consumption:1817.
[Tue Jul 11 03:05:42 2023]      emulate 'inc %%ecx'. energy consumption:60.
```