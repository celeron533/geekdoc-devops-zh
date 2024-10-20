# RAID 解释

> 原文：<https://acloudguru.com/blog/engineering/raid-explained>

RAID，即*独立磁盘冗余阵列*，是一种存储解决方案，旨在改善容错、存储管理和性能的某种组合。RAID 是一种存储虚拟化形式，它将多个物理磁盘组合成一个逻辑卷。RAID 的工作原理是以*镜像*或*分条*的方式保存数据(有时两种方式都有)，有或没有奇偶校验。*RAID 是如何设置的通过 *RAID 级别来记录。**

## 镜像 RAID

镜像 RAID 将保存的数据存储在两个驱动器上，提供了完美的副本。这是一个特别容错的解决方案，但 RAID 的容量减半，因为所有内容都保存两次。这确实允许更快的读取时间，因为两个并发的读取请求可以独立处理。相比之下，写入需要更长时间，因为数据会保存两次。

## 条带 RAID

条带化 RAID 通过强大的读写吞吐量在多个硬盘上保存数据，适用于需要多任务处理的情况。条带化通常与奇偶校验位一起用于检查错误。

### 平价

奇偶校验位是添加到数据串末尾的一位，用于错误检查。但是，奇偶校验位只能*检查*的错误，而不能纠正错误。尽管如此，当与数据分条一起使用时，奇偶校验位可以与其他磁盘上的数据一起重建原始数据。阵列中可以出现故障和重建的磁盘数量取决于 RAID 级别。

## RAID 级别

尽管这里列出的不仅仅是 RAID 级别，但 RAID 1-6 和 RAID 10 通常是最常被提及的。

### ![Raid 0](img/a011a855fee311e37fd06e9b39a22529.png)

### RAID 0

RAID 0 不提供额外的容错或冗余，但旨在提高驱动器的吞吐量。使用条带化将数据保存到磁盘，没有镜像或奇偶校验，将所有数据均匀分布在磁盘上。![Raid 1](img/a23bf519ddc08c44e729a2f17fd03e95.png)

### RAID 1

与 RAID 0 相反，RAID 1 使用*镜像*，没有分条或奇偶校验。这允许增加冗余，如上所述，具有改进的读取时间和降级的写入时间。

### ![RAID 2](img/953a4a7f9faf1cd6ab683092b4b92ac7.png)

### RAID 2

如今很少使用，RAID 2 使用带[汉明码](https://en.wikipedia.org/wiki/Hamming_code)奇偶校验的比特级条带化。内部磁盘的所有旋转都是同步的，每个连续的数据位都存储在不同的驱动器上。

### ![RAID 3](img/362ffaba0453b0d9c26d3bec001e012a.png)

### RAID 3

RAID 3 也不常见，它使用带奇偶校验的*字节*级条带化。与 RAID 2 一样，所有磁盘轮换都是同步的，数据也是分条的，因此每个连续的字节都在不同的驱动器上。奇偶校验位保存在专用磁盘上。![RAID 4](img/2bed1ec25530fa7049a39c44017891f2.png)

### RAID 4

与前两种 RAID 不同，RAID 4 使用带有专用奇偶校验的块级条带化，将预定大小的数据块保存到每个磁盘；一个磁盘专用于奇偶校验位。RAID 4 还为用户提供了并行性的好处，其中单个读/写操作*不需要*跨越所有驱动器来读取数据；这允许同时运行更多的操作。

### ![RAID 5](img/75fa85be46a45df2b48d0a5308b7bf0e.png)

### RAID 5

RAID 5 使用数据块级条带化，仅支持分布式奇偶校验，这意味着奇偶校验位分布在所有驱动器上。RAID 5 至少需要三个磁盘，最多一个磁盘出现故障也不会影响数据；但是，如果第二个磁盘出现故障。![RAID 6](img/4c76c7c686f2a0f061f8b0c02a6f7624.png)

### RAID 6

与 RAID 5 一样，RAID 6 也使用带奇偶校验的块条带化，但使用的是*双*奇偶校验，这意味着为每个数据字符串保存了两个奇偶校验位。这允许额外的容错，以及最多两个故障磁盘。然而，这是以更高的性能需求为代价的。![RAID 10](img/e1c978b878f201f5b67753bf2e7f63e0.png)

### RAID 10

RAID 10 将数据分条与镜像相结合，提供了强大的容错能力。多个驱动器可能会出现故障，只要没有镜像丢失所有驱动器，就可以重建数据。