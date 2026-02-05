
## References

1. [Failing to Reach DDR4 Bandwidth](https://ashvardanian.com/posts/ddr4-bandwidth/)


## Notes

* latency: [ref](https://www.crucial.com/articles/about-memory/difference-between-speed-and-latency)
	- CAS latency - he total number of clock cycles the data must go through.
	- latency (ns) = clock cycle time (ns) x number of clock cycles
	- Latency is best measured in nanoseconds, which is a combination of speed and CAS latency.
	- Example: because the latency in nanoseconds for DDR4-2400 CL17 and DDR4-2666 CL19 is roughly the same, the higher speed DDR4-2666 RAM will provide better performance.
	```
	DDR4-2400 CL17: l=2/2.400 * 17 = 14.16 ns
	DDR4-2666 CL19: l=2/2.666 * 19 = 14.25 ns
	```

## PCI-E Speed

* transfer rate - each lane can transmit 1 bit per transaction.
* line code - encoding scheme. 8b/10b means that 10 bits must be sent for every 8 bits transmitted.

| Generation | transfer rate (GT/s) | bandwidth per lane (GB/s) | line code (bits) |
|------------|----------------------|---------------------------|------------------|
| Gen 1      |  2.5                 | 0.25                      | 8 / 10           |
| Gen 2      |  5                   | 0.5                       | 8 / 10           |
| Gen 3      |  8                   | 1                         | 128 / 130        |
| Gen 4      | 16                   | 2                         | 128 / 130        |
| Gen 5      | 32                   | 4                         | 128 / 130        |
| Gen 6      | 64                   | 8                         | 1 / 1            |

Links:
* [PCIE1.0-6.0 Interface Bandwidth & Speed Calculation](https://www.diskmfr.com/pcie-interface-bandwidth-speed-calculation/)
* [Your Ultimate Guide to Understanding PCIe 6.0](https://www.onlogic.com/blog/your-ultimate-guide-to-understanding-pcie-6-0/)

Notes:
* PCI-E Gen 5 x16 has 64GB/s bandwidth which near to DDR5-5600 (89 GB/s)
* PCI-E Gen 3 x16 has 16GB/s bandwidth which less than bandwidth of DDR4-3200 (50 GB/s)


## Memory Speed

|  name   | transfer rate (MT/s) | bit width | clock (MHz) | bandwidth (GB/s)  | per 32bit (GiB/s)  | energy (pJ/bit) |
|---------|----------------------|-----------|-------------|-------------------|--------------------|------------------|
| LPDDR3  | 1600                 | 32        | 800         | 6.4               | 5.96               |                  |
| LPDDR3E | 2133                 | 32        | 1067        | 8.5               | 7.95               |                  |
| LPDDR4  | 3200                 | 64        | 1600        | 25.6              | 11.9               |                  |
| LPDDR4X | 4267                 | 64        | 2133        | 34.1              | 15.9               |                  |
| LPDDR5  | 6400                 | 32        | 3200        | 25.6              | 23.8               |                  |
| LPDDR5X | 8533                 | 32        | 4267        | 34.1              | 31.8               |                  |
| DDR3    | 1600                 | 64        | 800         | 12.5              | 5.96               |                  |
| DDR4    | 2400                 | 64        | 1200        | 19.2              | 8.94               |                  |
| DDR4    | 3200                 | 64        | 1600        | 25.6              | 12.8               |                  |
| DDR5    | 5120                 | 64        | 2560        | 40.9              | 19.1               |                  |
| GDDR4   | 1700                 | 32        | 868         | 6.9               | 6.3                |                  |
| GDDR5   | 4K                   | 32        | 1000        | 16.0              | 14.9               |                  |
| GDDR5X  | 8K                   | 32        | 1000        | 32.0              | 29.8               |                  |
| GDDR6   | 11K                  | 32        | 1375        | 44.0              | 41                 | 15               |
| GDDR6X  | 19K                  | 32        | 1188        | 76.0              | 70                 | 14               |
| GDDR7   | 48K                  | 32        | 1875        | 96                |                    | 8                |


Calculate bandwidth:
```
transfer_rate (MT/s) * bit_width * channel_count / 8 = bandwidth (MB/s)
transfer_rate (MT/s) * memory_bus / 8 = bandwidth (MB/s)
channel_count = memory_bus / bit_width
```


## USB speed

| name                | speed (Gbit/s) | latency |
|---------------------|----------------|---------|
| USB 2.0             | 0.48           | yes     |
| USB 3.0             | 5              | yes     |
| USB 3.1             | 10             | yes     |
| USB 3.2             | 20             | yes     |
| USB 4               | 40             | yes     |
| USB 4 2.0           | 80             | yes     |
| Thunderbolt 2       | 20             | yes     |
| Thunderbolt 3       | 40             | yes     |
| Thunderbolt 4       | 32-40          | yes     |
| Thunderbolt 5       | 32-120         | yes     |
| OCuLink PCIe 4.0 x4 | 64             | no      |
