# NEU-OS----
文件管理系统




课 程 设 计 报 告




设计题目：高级的文件管理系统

班    级：计算机1904
组长学号：20194723
组长姓名：郭恩铭
指导教师：林树宽
设计时间：2022年6月




设计分工
组长学号及姓名：20194723 郭恩铭
分工：主要负责中层的实现，主要包括目录相关操作的实现，包括mkdir、rm、ls等基础操作，以及剪切、复制、链接，查询，寻址方式的设计和实现等扩展功能，还实现了底层中成组链接分配功能。
组员1学号及姓名：20194695王家兴
分工：主要负责底层的实现，整体的系统架构及接口设计。主要包括模拟磁盘块的随机读写、底层文件结构的设计和实现、用户系统的设成和实现、其他系统功能的设计。
组员2学号及姓名：20194711巩钊旭
分工：主要负责高层的实现，面向用户的指令集设计。主要包括高层指令到中低层的解析和连接，实现完善的错误处理系统，完成部分指令集文档的编写。
组员3学号及姓名：20194801曾佳毅
分工：主要负责文档编辑器的实现。通过调用系统底层信号，实现文档的读取和写入，同时实现了按键的防抖以及基本权限的设计和实现。
目录
目录	3
1   概述	6
2   课程设计任务及要求	8
2.1 设计任务	8
2.2 设计要求	8
3.1 系统总体结构	9
3.2 文件系统底层模块	10
3.2.1 模块功能	10
3.2.2 数据结构	10
3.2.3 算法实现	18
3.3 文件系统中层模块	23
3.3.1 模块功能	24
3.3.2 数据结构	24
3.3.3 接口设计	25
3.3.4 算法实现	31
3.4 文件系统高层实现	35
3.4.1 模块功能	35
3.4.2 数据结构	35
3.4.3 模块流程	37
4  程序设计与实现	42
4.1 signin设计	42
4.1.1程序说明	42
4.1.2 实验结果	42
4.2 mkdir设计	43
4.2.1程序流程图	43
4.2.2程序说明	43
4.2.3实验结果	43
4.3 cd设计	45
4.3.1 程序流程图	45
4.3.2 程序说明	45
4.3.3 实验结果	45
4.4 ls设计	47
4.4.1 程序流程图	47
4.4.2 程序说明	47
4.4.3 实验结果	48
4.5 文件touch设计	49
4.5.1 程序流程图	49
4.5.2 程序说明	49
4.5.3 实验结果	50
4.6 文件open设计	50
4.6.1 程序说明	50
4.6.2 实验结果	50
4.7 文件write设计	51
4.7.1 程序说明	51
4.7.2 实验结果	51
4.8 文件read设计	52
4.8.1 程序流程图	52
4.8.2 程序说明	53
4.8.3 实验结果	53
4.9 文件close设计	54
4.9.2 程序说明	54
4.9.3 实验结果	54
4.10 级联rm设计	55
4.10.1 程序流程图	55
4.10.2 程序说明	55
4.10.3 实验结果	55
4.11 signout设计	57
4.11.1 程序说明	57
4.11.2 实验结果	57
4.12 format设计	57
4.12.1 程序说明	57
4.12.2 实验结果	58
4.13 copy设计	59
4.13.1 程序流程图	59
4.13.2 程序说明	59
4.13.3 实验结果	60
4.14 cut设计	62
4.14.1 程序流程图	62
4.14.2 程序说明	62
4.14.3 实验结果	63
4.15 paste设计	65
4.15.1 程序流程图	65
4.15.2 程序说明	65
4.15.3 实验结果	65
4.16 软连接设计	66
4.16.1 程序说明	66
4.16.2 实验结果	66
4.17 硬连接设计	68
4.17.1 程序说明	68
4.17.2 实验结果	68
4.18 重命名设计	70
4.18.1 程序流程图	70
4.18.2 程序说明	70
4.18.3 实验结果	70
4.19 级联（模糊）查找设计	72
4.19.1 程序流程图	72
4.19.2 程序说明	72
4.19.3 实验结果	73
4.20 用户注册设计	74
4.20.1 程序说明	74
4.20.2 实验结果	74
4.21 shutdown设计	75
4.21.1 程序流程图	75
4.21.2	程序说明	76
4.21.3 实验结果	76
4.22 debug设计	77
4.22.1 程序说明	77
4.22.2 实验结果	77
4.23 修改密码设计	78
4.23.1 程序说明	78
4.23.2 实验结果	78
4.24 help设计	79
4.24.1 程序流程图	79
4.24.2	程序说明	79
4.24.3 实验结果	80
4.25 用户列表展示及其root用户管理设计	81
4.25.1 程序说明	81
4.25.2 实验结果	81
4.26 更改管理员权限	81
4.26.1 程序说明	81
4.26.2 实验结果	82
4.27 查看磁盘空占用情况	82
4.27.1 程序说明	82
4.27.2 实验结果	82
4.28 删除指定用户	85
4.28.1 程序说明	85
4.28.2 实验结果	85
4.29 文本编辑器设计	87
4.29.1 程序流程图	87
4.26.2 程序说明	89
4.26.3 实验结果	89
5  结论	92
6  参考文献	92
7  收获、体会和建议	93

1   概述
项目组整体完成了一个功能全面，容错率高的文件系统。整个系统提供了完善的用户登录，登出的控制。其中对于不同用户可以修改自己密码，还能够完成对于root目录下的管理员操作，以及全部用户的管理。通过构建C++的用户类完善了整个文件系统的用户端。
整个课程设计贯穿了四大思路，“一切皆文件”、“隐式链接”、“成组链接分配”、“模拟磁盘外存”。其中底层设计，参考了Linux的“一切皆文件”的思路进行设计。文本文件、目录、软连接等皆使用文件方式进行存储，并且使用统一的读写控制。其中对于超大文件的存储，使用了隐式链接。本系统设计了流文件的顺序存取，因此选用了隐式链接的方式来保存全部文件。为了方便文件扩展，不会有磁盘碎片化的问题。对于空闲块的管理，使用了成组链接分配的设计方案，空白块号尽管登记，但却不占用额外的空间，只借用每组的最后一个空白块。这种空闲管理方式不仅便于回收，还可以节省时间。实际的底层模拟磁盘块设计，采用了一个4MB大小的二进制文件模拟磁盘，每个块大小为1KB，一共4096个块，磁盘支持随机读写，在读写的时候不需要把整个4MB的磁盘读入缓存。
项目的寻址方式还原了Linux的多重寻址模式，不仅仅支持根目录寻址、用户目录寻址、当前目录寻址以及父级目录寻址等四种方式。在功能方面项目组不仅实现了全部验收表中的基本功能，其中包括目录的ls、cd、文件和目录的新建、文件的编辑write、open、read等，还完成创新功能，查找、文件目录的复制、文件目录的粘贴、文件目录的剪切、级联删除、级联模糊查找、软连接和硬链接等功能，还实现了mv和rename等功能。
除此之外，系统还完成了具有充分报错的前端界面，以及还原了一套Linux的指令解析，用户可以在前端输入如同Linux的指令一样，完成目标的操作。项目组还从底层完成了文本编辑器，完全是从底层进行了光标变化，以及按钮防抖等功能。
2   课程设计任务及要求
2.1 设计任务
在下列内容中任选其一：
1、多用户、多级目录结构文件系统的设计与实现；
2、WDM驱动程序开发；
3、存储管理系统的实现，主要包括虚拟存储管理调页、缺页统计等；
4、进程管理系统的实现，包括进程的创建、调度、通信、撤消等功能；
5、自选一个感兴趣的与操作系统有关的问题加以实现，要求难度相当。
2.2 设计要求
1、在深入理解操作系统基本原理的基础上，对于选定的题目，以小组为单位，先确定设计方案；
2、设计系统的数据结构和程序结构，设计每个模块的处理流程。要求设计合理；
3、编程序实现系统，要求实现可视化的运行界面，界面应清楚地反映出系统的运行结果；
4、确定测试方案，选择测试用例，对系统进行测试；
5、运行系统并要通过验收，讲解运行结果，说明系统的特色和创新之处，并回答指导教师的提问；
6、提交课程设计报告。
 
3   算法及数据结构
3.1 系统总体结构
 
3.2 文件系统底层模块
3.2.1 模块功能
	本模块为文件系统底层模块，主要功能是和作用是模拟物理磁盘进行随机读写，包括不同文件存储结构的设计、文件存取的功能实现、空闲磁盘块分配和回收等。
	底层设计时，参考Linux的“一切皆文件”的思路进行设计。文本文件、目录、软链接等皆使用文件方式存储，并使用统一的读写控制。系统大部分文件为流文件，仅支持顺序存取，因此选用隐式链接的方式来保存超大型文件。方便文件扩展，不会有磁盘碎片化的问题。空闲块的分配和回收则选用成组链接法，空白块号登记不占用额外空间，只借用每组的最后一个空白块。 当前可分配的物理块号存放在卷资源表中，因此绝大部分的分配和回收工作是在主存中进行，可以节省时间。我们使用一个4MB大小的二进制文件模拟磁盘，每个块大小为1KB，一共4096个块，磁盘支持随机读写，在读写时不需要把整个4MB的磁盘读入缓存。

3.2.2 数据结构
我们在设计时首先抽象出 “文件”，它是最基础的存储结构，它包括报头和报文，其中报头包括占用标记、计数器、下地址、创建时间和修改时间。不同的文件的报文不同，报文也就是文件的内容（content）。我们设计每一块的大小为1024字节，其中报头占12字节。对于小文件来说，一块可以存储所有的content，则其下地址为FF；对于超大型文件来说，一个文件可能需要多块才能存储，那么就可以通过下地址来形成链表作隐式连接，最后一块的下地址为FF。
	我们将文本文件、目录、索引节点、用户都抽象为文件的派生类。我们将目录也视为特殊的文件。
	下面展示各种文件的存储结构：
 
基础文件结构
 
目录文件结构

 
索引节点文件结构
 
用户文件存储结构
基础文件类声明：
class File {
public:
	FileType type;							// 文件类型
	int created;							// 创建时间
	int modified;							// 修改时间
	short counter = 1;						// 计数器
	File(FileType t = FileType::ftxt) :type(t) {}
	File(FileType t, int c, int m) :type(t), created(c), modified(m) {}
	virtual EncodeBytes encode();			// 编码
	virtual void decode(short block);		// 解码
	virtual int sizeOf() = 0;				// 内容大小
	virtual byte* contentEncode() = 0;		// 内容编码
	virtual void contentDncode(byte* bytes, int size) = 0;	// 内容解码
	short save(short block = -1);
	static int remove(short block);
	static void addCounter(short block);
};


目录文件类声明：
class CatalogRecord {
public:
	string name;
	FileType type;
	// 块号
	short block;
	uint8 id;
	byte* encode();
	CatalogRecord(string name = "", FileType type = FileType::undefined, short block = -1, uint8 id = -1) :
		name(name), type(type), block(block), id(id) {}
	static CatalogRecord decode(byte* bytes);
	int sizeOf();
	friend ostream& operator << (ostream& out, CatalogRecord record) {
		out << "(" << record.name << "," << FileTypeString(record.type) << "," << (short)record.block << "," << (short)record.id << ")";
		return out;
	}
};


class Catalog :File {
public:
	short parent;
	vector<CatalogRecord>recodes;
	EncodeBytes encode() override {
		return File::encode();
	}
	void decode(short block) override {

		File::decode(block);
	}
	Catalog(initializer_list<CatalogRecord>l = {}) :recodes(l) {}
	Catalog(vector<CatalogRecord>l) :recodes(l) {}
	int sizeOf() override;						// 内容大小
	byte* contentEncode() override;				// 内容编码
	void contentDncode(byte*, int) override;	// 内容解码
	short save(short block = -1) {
		return File::save(block);
	}
	friend ostream& operator << (ostream& out, Catalog catalog) {
		out << "[";
		if (catalog.recodes.size() > 0) {
			out << catalog.recodes[0];
		}
		for (int i = 1; i < catalog.recodes.size(); i++) {
			out << "," << catalog.recodes[i];
		}
		out << "]";
		return out;
	}
};


索引节点文件类声明：
class Inode {
public:
	uint8 block;
	uint8 id;
	pointer addr;
	Authorities authorities;
	uint8 getAuthority(uint8 user = USER);
	void addAuthority(uint8 user, uint8 auth);
	void delAuthority(uint8 user, uint8 auth);
	Inode() = default;
	Inode(uint8 id, pointer addr, Authorities authorities) :id(id), addr(addr), authorities(authorities) {}
	Inode(uint8 id, pointer addr) :Inode(id, addr, {}) {}
	int sizeOf();
	byte* encode();
	static Inode decode(byte* bytes);
};

class InodeBlock {
public:
	uint8 block;
	pointer next;
	umap<uint8, Inode>inodes;
	InodeBlock() = default;
	InodeBlock(uint8 block, pointer next, umap<uint8, Inode>inodes) :block(block), next(next), inodes(inodes) {}
	InodeBlock(pointer next, umap<uint8, Inode>inodes) :InodeBlock(1, next, inodes) {}
	InodeBlock(uint8 block, pointer next) :InodeBlock(block, next, {}) {}
	int sizeOf();
	byte* encode();
	static InodeBlock decode(short block);
	void write();
	Inode& operator [](int i) {
		return inodes[i];
	}
};


用户文件类声明：
class User {
public:
	uint8 _id;
	string name;
	string pass;
	int sizeOf();
	byte* encode();						// 内容编码
	static User decode(byte* bytes);	// 内容解码
	User() :_id(255) {}
	User(uint8 _id, string name, string pass) :_id(_id), name(name), pass(pass) {}
	friend ostream& operator << (ostream& out, User user) {
		out << "(" << (short)user._id << "," << user.name << "," << user.pass << ")";
		return out;
	}
};

class UserFile :File {
public:
	umap<short, User>users;
	EncodeBytes encode() override {
		return File::encode();
	}
	void decode(short block) override {
		File::decode(block);
	}
	UserFile(umap<short, User>l = {}) :users(l) {}
	int sizeOf() override;						// 内容大小
	byte* contentEncode() override;				// 内容编码
	void contentDncode(byte*, int) override;	// 内容解码
	short save(short block = -1) {
		return File::save(block);
	}
	friend ostream& operator << (ostream& out, UserFile userFile) {
		out << "[";
		if (userFile.users.size() > 0) {
			out << userFile.users[0];
		}
		for (int i = 1; i < userFile.users.size(); i++) {
			out << "," << userFile.users[i];
		}
		out << "]";
		return out;
	}
};


模拟磁盘类声明：
class Disk {
public:
	static void init();
	static byte* read(short block);
	static void write(short block,string str);
	static void write(short block, byte* str);
	static bool isEmpty(short block);
	static short getNext(short block);
	/*
	* mode == 0: 返回空闲块
	* mode == 1: 返回占用块
	* mode == 2: 返回所有块
	*/
	static vector<pair<short, bool>> list(int mode);
};
空闲磁盘块分配类：
class FreeBlock {
	static vector<short>S;//表示空闲块号栈
	static short allocateOneBlock();
	static void freeOneBlock(int BlockNo);
	static vector<short> readFreeBlock(short block);
	static void writeFreeBlock(short block, vector<short> blocks);
public:
	static void format();
	static void init();//基本想法就是吧空闲块号栈读入内存
	static void over();//把空闲块号栈写入外存
	static vector<short>allocateBlocks(int num);
	static int occupy;
	static void freeBlocks(vector<short>Blocks);
};

3.2.3 算法实现
3.2.3.1 磁盘初始化
	磁盘初始化的工作非常简单，直接将全零值存入磁盘。磁盘初始化不等于磁盘格式化，磁盘格式化并不会简单粗暴的将全零值存入磁盘。磁盘初始化模拟的是现实生活中磁盘刚被生成出来时全新的状态。

3.2.3.2磁盘块读取
	该函数用于把指定块中的数据读取出来，读取时块号将由其他函数给出，读取出来的数据也是二进制流，这个函数不会对读取的数据做任何处理，将直接返回出来，供其他模块使用。

3.2.3.3磁盘块写入
	该函数用于在指定块中写入数据，写入的数据为二进制流，写入的块号以及二进制流将由其他模块给出。

3.2.3.4判断磁盘块是否处于占用状态
	该函数用于判断指定磁盘块是否为占用状态，调用该函数后，将会且只会读取磁盘块中的“占用标记”，并返回其占用情况，这个过程不会读取其他多余的东西到内存。

3.2.3.5获取下地址
	该函数用于获取指定块的下地址，调用该函数后，将会且只会读取磁盘块中的“下地址”，并返回其值，这个过程不会读取其他多余的东西到内存，当该文件没有下地址时，返回结果为FF。

3.2.3.6磁盘块状态
	调用该函数可以返回空闲、占用或所有磁盘块，并返回其状态。

3.2.3.7文件保存
	由于在设计和编码时使用面向对象的思想，将所有类型的文件都抽象为基础文件的派生类，因此所有文件派生类的保存过程都是一样的。
	文件派生类首先会调用encode函数，这个函数是保存过程的起点，他负责将文件的内容编码为二进制流。接着会获取内容的长度，因为如果内容长度过长可能导致一个块存不下。计算需要的磁盘块数，然后分配空闲磁盘块，分配成功则会开始填写，程序每填写一块就会判断内容是否填写完毕，当内容全部填写完毕后会从内存写入磁盘。

 

3.2.3.8文件读取
	由于在设计和编码时使用面向对象的思想，将所有类型的文件都抽象为基础文件的派生类，因此所有文件派生类的读取过程都是一样的。
	文件派生类首先读取块，然后读取到文件块的下地址，如果其为FF，说明文件为单块存储，否则继续读取下一块文件块，直到下地址为FF。然后将多个块的内容进行拼接，再经过解码就可以成功读取文件。
 

3.2.3.9索引节点读取
   索引节点的读取与普通文件有些区别。本系统设计的所有文件都是流文件形式，支持顺序读写，而索引节点的文件还支持索引读取，根据目录中保存的属性可以读取指定索引节点。一个索引节点文件中存储多个索引节点，因此想要获取一个索引节点除了获取文件块号外，还需要获取文件内编号。使用编号而不是偏移量来寻找节点是为了方便进行修改和删除，使用编号管理，进行修改和删除时，不需要对其他节点进行修改。
 
3.2.3.10 成组链接法空闲磁盘分配
   成组链接的整体结构如下图所示，其中通常把外存的0号块当成系统块，不进行使用，并且当作记录内存栈的系统块。
 
成组链接的分配原理如下流程图，再分配组长块的时候需要做特殊的处理。需要将组长块中的内容写入到内存栈之中。
 


3.2.3.11 成组链接法空闲磁盘回收
    调用此函数需要将BlockNo传入，表示需要释放的块的编号。首先需要判断是否当前空闲栈即将满，如果当前栈即将满，则需要将栈中的 信息先放到一个空闲块中。如果当前空闲栈没有即将达到满栈的状态，则需要向空闲块中插入一个当前块号，并且使得栈的数量自增。
 
 

3.3 文件系统中层模块

3.3.1 模块功能
系统的中层模块的主要功能在于利用全部的数据结构，其中包括了在完成底层数据结构设计过程中所构造的File类别，以及Inode结点类，以及由于File进行派生，产生的Catalog类别以及Ftxt类别，去实现全部功能。在中层模块是利用各种功能实现目录和文件之间索引的。在实现过程中需要建立目录树，由于整个系统所构建的是一个多级目录索引搜索，因此整棵树较为庞大。
由于系统在完善过程中，构建了多种级联功能，因此在算法部分较多地使用了树的先根遍历以及后根遍历。
最终整个模块能够实现验收表里面的全部基础功能，以及自增第扩展功能。主要在模块功能部分完成的。
3.3.2 数据结构
在数据结构部分，这一部分广泛使用了底层中的Catalog类别，以及Inode类别还有Ftxt类别。通过这些类别进行功能上的实现 。在系统刚刚登录初始化的过程中，将根目录“/”，读入系统的目录缓存之中。为了能够更加方便地，快速地 ，避免每次都需要调用外存进行目录块的访问，建立了内存的目录缓存。如下图一所示。其中对应的short表示块号，块号中存储着对应的目录。如果对应的map[short]不为空，则直接从内存中读取目录；相反，则从外存中进行目录的读取。
 
在实现过程中，设计了复制，剪切和粘贴的功能，其中运用了一个Status类标明当前的状态，为了复制过程进行指示。
 


3.3.3 接口设计
（1）删除接口
 
（2）重命名接口
 
（3）创建文件接口
 
（4）创建目录接口
 
（5）移动接口

 
（6）展示目录接口
 
（7）展示目录接口
 
（8）复制/剪切接口
 
（8）粘贴接口
 
（9）软硬链接接口
 
（10）文件打开接口
 
（11）文件关闭接口
 
（12）读取文件接口

 
（13）写文件接口
 
（14）文件查找接口
 



3.3.4 算法实现
算法设计部分由于使用了许多复杂算法这里举例复杂的算法过程进行展现。 
（1）	多种地址索引原理
由于传入的路径错综复杂，我们设计的路径可以支持各种路径寻址，因此我们需要将全部的路径全都转化成为标准的从根路径往下的形式，进行判断之后 。
 
（2）级联创建文件以及目录
在整个课程设计的过程中许多都需要用到级联创建，从mkdir到mv中的dest地址，再到paste下的dest地址，如果没有指定的路径，则系统需要支持级联创建，把所需要的目录文件夹都新建了。对于级联创建来说，需要首先切分一个路径，对于”/gem/happy/sad/1.txt”,对于此路径，在gem下不存在happy文件夹，因此在切分路径的过程中，首先需要找到第一个不存在的目录，然后在级联创建到最后一个’1.txt’的位置后，则需要完成递归结束。之前的则可以使用递归创建。
级联只创建目录，则不需要特殊对于最后一层进行判断。
 
如果级联进行创建文件，则需要对于最后一层进行特殊判断。
 
（3）级联删除文件以及目录
前文讲述了，级联创建的过程，是一个先根遍历，只有把父级目录先创建完成之后，才能够进行子级目录的创建，但是对于级联删除的过程来说，是一个后根遍历，也就是说，只有把子目录全都删除干净之后，才能进行父目录的删除。
由于级联删除十分复杂，需要考虑对于硬链接中的结点数量，这一部分封装在底层了，每次调用Ftxt类下的文件删除函数，会自动判断，这减轻了中层的判断逻辑。
但是还需要注意，文件打开表下的文件，如果某一个文件已经打开了，则不能删除。这里涉及的逻辑是，在级联删除的过程中，如果遇到此种情况，则进行整条枝条的保留。
 
（4）级联复制文件以及目录
级联复制是整个递归内容中最复杂的部分，如果复制的是一个目录的话，则需要进行该目录下的所有使用的磁盘块的复制，因此十分复杂。整个级联复制也是一个先根遍历，需要先将父级中的目录建立一个备份，之后才能去操作子目录下的占用块。 

 
（5）级联模糊搜索文件
级联模糊搜索，是一个比较有用的功能函数，可以直接查询某一个路径下的全部.txt文件，这对于我们统计文件之类的具有很好的功能。
 





3.4 文件系统高层实现
3.4.1 模块功能
此模块面向用户，通过对用户输入的指令，进行词法、语法分析，若用户输入的指令错误，报出对应的错误提示；若指令合法，按照指令功能调用对应文件接口。由于部分指令是由中层文件系统接口组合后的结果，因此还需要进行接口组合，以便给用户提供扩展的指令。
3.4.2 数据结构
此部分用到的数据结构为vector，通过对输入指令分割，存储后进行分析，此部分在memu.h中声明了menu类，包含各种提供给用户的接口函数，该类声明如下：
#pragma once
#include <sstream>
#include "base.h"
using namespace std;
class Menu {
public:
	static void start();
	static vector<string>getLine();
	static void debug(bool flag);
	static void signin();
	static void signup();
	static void mkdir(vector<string> instruction);
	static void touch(vector<string> instruction);
	static void cd(vector<string> instruction);
	static void ls(vector<string> instruction);
	static void debug(vector<string> instruction);
	//shutdown format clear
	static void rename(vector<string> instruction);
	static void rm(vector<string> instruction);
	static void cp(vector<string> instruction);
	static int cpDir(vector<string> instruction);
	static int cpFile(vector<string> instruction);
	static void paste(vector<string> instruction);
	static void mv(vector<string> instruction);
	static void cut(vector<string> instruction);
	static int cutDir(vector<string> instruction);
	static int cutFile(vector<string> instruction);
	static void ln(vector<string> instruction);
	static void open(vector<string> instruction);
	static void close(vector<string> instruction);
	static void read(vector<string> instruction);
	static void write(vector<string> instruction);
	static void help();
	static void pass(vector<string> instruction);
	static void su();
	static void userlist();
	static void disklist(vector<string> instruction);
	static void delUser(vector<string> instruction);
	static void test(vector<string> instruction);
	static void find(vector<string> instruction);
};
3.4.3 模块流程
 
接下来展示从用户输入一条指令到最终实现相应的效果，高层做了哪些工作：
1.	对于非组合多参数指令，如cp -r [dirA] [dirB]，其工作流程如下：
 
前面的gzx:/home/gzx$用来展示当前用户、当前工作路径，通过改变窗口句柄的颜色，然后打印当前用户名，之后调用中层文件部分提供的CatalogController::path，打印出当前工作目录。此部分为每次必打印的东西，之后便不做展示。
SetConsoleTextAttribute(outHandle, 0x0A);
		cout << USER_NAME;
		SetConsoleTextAttribute(outHandle, 0x07);
		cout << ":";
		SetConsoleTextAttribute(outHandle, 0x03);
		cout << CatalogController::path;
		SetConsoleTextAttribute(outHandle, 0x07);
		cout << "$ ";
当用户输入cp -r test时，调用菜单中封装的getline函数，进行单词划分。如遇到空格，代表单词结束，将该单词加入vector中，str置空，继续识别单词，若不是空格也不是换行，则当前单词未结束，str+=c；若遇到换行，代表用户输入完成，将最后一个单词加入vector中，同时返回该vector。此vector便是我们之后进行语法分析的数据结构。
 
接下来，vector已经存到了instruction变量中，我们对首单词判断，若是cp，进入高层cp函数。
 
否则判断是不是其他已知指令，若都不是，则报出错误提示，虽然我们的报错系统非常完美，但是对于错误指令肯定是无法识别的，直接报出不存在即可。
 
进入cp函数后，若vector instruction长度小于2，提示cp指令有误
 
若长度大于等于2，继续判断，因为cp指令有四种组合方式：
cp [file]	cp [file] [dir]	cp -r [dir]		cp -r [dirA] [dirB]
具体是文件操作的不带-r参数，还是带-r的目录操作，我们继续往前看一个单词，若带-r，则确定为目录操作，具体是哪种目录操作，我们需要对instruction长度进行判断，长度为3，第一种，长度为4，第二种，长度其他，则指令错误，报出具体提示。
 
关于对只要为-r后长度为3或4默认判对的疑问，解答如下：
文件和目录都属于文件，目录是特殊的文件，若用户输入的是不是合法的已存在的目录或文件，则由中层进行判断，因此高层只需要对中层的文件接口返回值进行判断即可，若复制且粘贴的目标路径是否存在同名文件，也由中层做了处理，高层无需判断。
 
2.	对于非组合多参数指令，如cut -r [dirA] [dirB]，其工作流程如下：
 
首先仍需调用Menu::getLine()函数对字符进行单词划分，词法分析，之后调用cut函数。Cut函数中做的工作和上述cp指令一致，通过对长度已经是否-r判断是文件还是目录操作，之后便进入对应的分支进行中层函数调用，不做过多展示。但对于双参数的目录剪切，需要做额外的任务：
其本质相当于调用cp函数，指定iscut参数为true，即剪切版复制，之后再次调用paste函数进行粘贴，指定paste参数为目标路径即可。
 








4  程序设计与实现 
4.1 signin设计 
4.1.1程序说明
系统在开机时读取用户文件，用户输入用户名和密码后会在缓存中进行对比，如果存在用户名，且密码正确，则登录成功。

4.1.2 实验结果
输入signin指令进行用户注册，若两次密码不一致，报出错误，回到控制台：
 
若正确按照指引输入，则成功完成注册，并自动登录，进入该用户的工作目录/home/username
 
4.2 mkdir设计 
4.2.1程序流程图
 
4.2.2程序说明
整个mkdir可以进行目录的创建，由于支持了级联创建的功能，则需要进行创建的时候切分功能。找到第一个没有创建的位置，如果目录已经存在了则退出不再创建。如果以上两条都没满足，则正常进行级联创建目录。
4.2.3实验结果
输入mkdir指令创建目录，若指令错误，报出错误，回到控制台：
 
正确输入指令后，使用ls查看，os目录创建成功：
 
若目录下存在同名目录，报错：
 
Mkdir支持在任何目录下创建文件，下面为在根目录下创建os中的目录：
 
4.3 cd设计  
4.3.1 程序流程图
 
4.3.2 程序说明
在整个系统中需要存储curdir表示当前目录，因此在cd顺利的情况下需要将当前的目录获取到。如上的流程除了在判断的时候需要加入对于空目录的摒弃，如果非空则可以顺利进入。
4.3.3 实验结果
在4.2节中我们创建了os目录，接下来展示进入该目录并从该目录返回。
 
cd指令支持级联进入和级联返回，我们在os目录下再次创建一个lab目录，从home/gzx下直接进入lab：
 
级联返回：
 
若进入不存在的目录，报出错误提示：
 
4.4 ls设计 
4.4.1 程序流程图
 
4.4.2 程序说明
查看某一个目录下的内容这个功能十分重要，我们为了用户在前端能够更直观的观察，我们还对于每一种不同的“文件类型”进行了颜色区分，在逻辑方面，首先要将传入的千奇百怪的多种寻址的目录种类，转化成为标准形式。之后就将此目录传送给前端，以便于前端进行界面化展示。
4.4.3 实验结果
ls指令用以展示当前目录（不带参数）或者目标目录（带目录参数）下各个文件，不同种类文件以不同颜色展示，首先在工作目录下创建四种类型的文件，接着ls不带参数，结果如下：
 
ls指令支持带目录参数查询，即不进入目标路径也可查询目标路径下文件，在lab下创建一个文件，接着退回根目录查询，结果如下：
 
若ls查询的目录不存在，报出错误：
 
4.5 文件touch设计 
4.5.1 程序流程图
 
4.5.2 程序说明
整个touch可以进行文件的创建，由于支持了级联创建的功能，则需要进行创建的时候切分功能。找到第一个没有创建的位置，在递归的过程中，判断到最后一层的文件位置，根据用户尾缀进行类型赋值。
4.5.3 实验结果
touch 文件名创建文件：
 
若目录下已存在同名文件，报错：
 
4.6 文件open设计 
4.6.1 程序说明
逻辑上大同小异，首先判断文件路径是否真的存在之后，才能完成打开。
只有加入打开表的文件才有可能被后续的操作，其中包括读取文件和写入文件。
4.6.2 实验结果
打开目录下不存在的文件，报错：
 
Open参数有误，报错：
 
正确输入，则文件打开，将文件加入文件打开表中，此时赋予读权限，若赋予写权限，参数为-w：
 
4.7 文件write设计 
4.7.1 程序说明
逻辑上大同小异，首先判断文件路径是否真的存在之后，才能完成文件的读取。
只有加入打开表的文件才有可能被读取，但是在读取之前还需要判断该文件是否拥有读写权限，如果没有则无法对于此文件进行写操作，前端会进行报错。
4.7.2 实验结果
在4.6节中，我们以读权限打开了lab.txt，此时如要向文件写入，必然会被拒绝访问：
 
若write一个不存在的文件，报错：
 
若write一个未被打开的文件，报错：
 
正确按照流程以写权限打开一个文件后输入写指令，成功打开编辑器，我们写入hello world！，保存：
 
 
4.8 文件read设计 
4.8.1 程序流程图
这里流程图与4.7省略的流程图可以通用
 
4.8.2 程序说明
逻辑上大同小异，首先判断文件路径是否真的存在之后，才能完成文件的读取。
只有加入打开表的文件才有可能被读取，但是在读取之前还需要判断该文件是否拥有读写权限，如果没有则无法对于此文件进行写操作，前端会进行报错。

4.8.3 实验结果
4.7节中我们向lab.txt中写入了hello world！，接下来我们查看一下：
 
文件编辑器自动打开，显示内容，由于是读方式打开此文件，因此无法进行编辑：
 
读取一个不存在的文件，报错：
 
读取一个未被打开的文件，报错：
 
4.9 文件close设计 
4.9.2 程序说明
逻辑上大同小异，首先判断文件路径是否真的存在之后，才能完成打开。
对于加入打开表的指定文件，可以完成关闭的功能。之后回复文件的删除操作。不然对于加入打开表的文件不具有删除操作。
4.9.3 实验结果
我们将lab.txt文件打开后关闭：
 
如何验证文件已被关闭，很简单，用read指令看看能否打开即可，此时报错，提示文件未打开，成功关闭：
 
若关闭一个不存在的文件，报错：
 
4.10 级联rm设计 
4.10.1 程序流程图
 
4.10.2 程序说明
整个删除做到了级联删除，还能完成了对于文件打开表中的文件的保护功能。对于单个文件的删除，操作则比较简单，但是当传入任何不存在的目录或者文件，则系统会对此进行报错。
4.10.3 实验结果
在~/os/lab下创建两个文件，其中，1.txt已被打开：
 
接下来我们级联删除掉整个os目录：
 
这时我们ls查看一下~路径，发现os仍然存在：
 
此时再次查看os内部路径，os中的lab1目录已被删除，同时lab下2.txt也被删除，而1.txt仍然存在，因为其已被打开：
 
若删除文件，rm即可：
 
若rm不存在的文件或目录，报错：
 
若rm删除目录的参数不为-r，报错：
 
若rm已打开但未被关闭的文件：
 
4.11 signout设计 
4.11.1 程序说明
用户调用后，缓存中登录用户的信息将被清空
4.11.2 实验结果
退出当前的gzx用户：
 
4.12 format设计 
4.12.1 程序说明
    在系统初始化的时候，首先需要对于成组链接的复制，构建组长块内部的信息，而且在我们设计的环节中，还完成了有关的根目录的保存，构建了在”/”下面的根目录，并且向根目录中存了一个home文件夹，用来存储用户目录。
4.12.2 实验结果
执行format指令前，磁盘块中存储了一些信息：
 
执行format后：
 
再次登录，看能否登上去以前的账号：
 
4.13 copy设计 
4.13.1 程序流程图
 
4.13.2 程序说明
在系统进行copy函数的过程中，接口部分区分了对于文件的copy和目录的copy，copy只需要将信息存放在缓存中即可，如果是对于文件的copy，则需要在缓存剪切复制板的状态字中标记。
4.13.3 实验结果
cp分为1.cp [file] 2.cp [file] [dir] 3.cp -r [dir] 4.cp -r [dirA] [dirB]
1.	cp [file]
 
若文件不存在，报错：
 
2.	cp [file] [dir]
 
之后查看lab目录，成功完成拷贝：
 
若目标目录不存在，自动创建目录，并完成复制：
 
3.	cp -r [dir]
 
若目录不存在，报错：
 
若目录参数错误，不为-r，报错：
 
非法指令则直接报错：
 
4.	cp -r [dirA] [dirB]
 
目标目录不存在，自动创建目录，并完成复制：
 
4.14 cut设计 
4.14.1 程序流程图
 
4.14.2 程序说明
在系统进行cut函数的过程中，接口部分区分了对于文件的cut和目录的cut，cut只需要将信息存放在缓存中即可，如果是对于文件的cut，则需要在缓存剪切复制板的状态字中标记。

4.14.3 实验结果
cut分为1. cut [file] 2. cut [file] [dir] 3. cut-r [dir] 4. cut-r [dirA] [dirB]
1.	cut [file] 剪贴文件
 
若文件不存在，报错：
 
2.	cut [file] [dir] 
将lab.txt剪贴到test目录，之后ls查看当前目录，lab.txt文件消失，ls test，可以看到lab.txt成功完成剪贴
 
若文件不存在：
 
若目标路径不存在，自动创建目标目录：
 
3.	cut-r [dir] 
 
若目录不存在，报错，提示目录不存在：
 
4.	cut-r [dirA] [dirB]
将os目录剪切到lab目录下，ls查看当前目录，os目录消失，ls lab，可以看到os成功剪切。
 
若指令非法，报错：
 
4.15 paste设计
4.15.1 程序流程图
 
4.15.2 程序说明
   需要根据缓存中剪切板的状态字对于paste进行不同函数的调用，在以上流程图不赘述调用函数的内部逻辑。
4.15.3 实验结果
Paste可以指定目标路径也可以不指定，默认在当前目录下粘贴。粘贴需要先复制或者cut，假设前一步已完成，仅展示paste：
 
带目标路径的paste如下：
 
若之前未进行过复制或者单参数剪切，即缓冲区为空，报错：
 
若粘贴的文件或者目录已在目标目录存在同名，则失败：
 
4.16 软连接设计 
4.16.1 程序说明
软连接的逻辑是在对应的dest目录下面建立一个文件，这个文件是一个链接.link类型，并在这个link类型中保存对应的真实文件的地址。
需要判断src是否存在。
4.16.2 实验结果
将lab.txt软链接到lab目录下，可以看到lab目录下的lab.txt颜色为蓝绿色，代表其属性为link文件：
 
我们此时打开此文件，看看里面存储了什么，可以看到，存储了源文件的路径：
 
若软链接参数有误不为-s，报出错误：
 
若原文件不存在，报错：
 
若目标路径下已存在同名文件，报错：
 
若目标路径不是一个合法的目录名，报错：
 
若指令非法，报错：
 
4.17 硬连接设计 
4.17.1 程序说明
硬链接逻辑简单类似于剪切的操作，只不过剪切的操作需要将剪切src地址的父级目录中的记录删除，而硬链接则不需要，在底层的index结点中直接自增。
在完成此函数操作之前，还是需要对于硬链接的src目录进行判断。
4.17.2 实验结果
将lab.txt硬链接到lab目录下，可以看到成功硬链接，颜色为黄色，代表其实txt文件：
 
打开此硬链接的文件，可以看到内容为空，而不再是路径：
 
若目标路径下已存在同名文件，报错：
 
若原文件不存在，报错：
 
若目标路径不是一个合法的路径名：
 
4.18 重命名设计 
4.18.1 程序流程图
 

4.18.2 程序说明
重命名的环节中对于传入的名字参数不能是一个路径，也就是说不是”/df/dfa”的结构，一定要是一个名字，要进行报错。
并且还要保证，src路径是存在的。
4.18.3 实验结果
Rename包括文件重命名rename [file]和模流重命名rename -r [dir]：
1.	rename [file]
 
若原文件不存在：
 
若新文件名不是一个合法的文件名：
 
若新文件名已在当前目录下存在：
 
若指令非法：
 
2.	rename -r [dir]
 
若原目录不存在：
 
若新目录已在当前目录下存在：
 
若参数不是-r：
 
4.19 级联（模糊）查找设计 
4.19.1 程序流程图
 
4.19.2 程序说明
    在查询之前需要判断是否存在该路径，根据前端的指令调用不同的函数。
4.19.3 实验结果
查找有四种：
1.	find [file] [dir] 普通查找
 
若输入非法：
 
2.	find -r [dile] [dir] 级联查找，我们在根目录下创建1.txt，也在lab和new
目录下创建1.txt，进行级联查找：
 
 
3.	find -a [dile] [dir] 模糊查找
对txt文件进行查找：
 
4.	find -ar [dile] [dir] 级联模糊查找
对txt文件进行级联查找：
 
4.20 用户注册设计 
4.20.1 程序说明
系统在开机时读取用户文件，用户输入用户名和密码后会在缓存中进行对比，必须为存在的用户名才可以创建。

4.20.2 实验结果
注册可以发生在系统运行的任何时候，输入signin指令后按照指引进行注册，密码需要输入两次：
 
若两次密码不一致，报错：
 
若用户已存在，报错：
 
若用户名过长，报错：
 
若密码过长，报错：
 

4.21 shutdown设计 
4.21.1 程序流程图
shutdown即为安全关闭系统，完成后续磁盘操作，由于整个控制台运行在main函数，main函数卡在菜单的死循环中，因此只需要在shutdown中完成return即可，后续交由main函数后续操作来处理。
 
4.21.2	 程序说明
shutdown进行return即可，回到主函数运行后续结束操作。
4.21.3 实验结果
 
4.22 debug设计 
4.22.1 程序说明
在程序内部的磁盘读取、保存、索引节点的读取、保存等都设置有调试输出，在用户打开debug功能后，会在界面中看到调试信息。

4.22.2 实验结果
debug开启后，能够看到i节点的相关操作和底层磁盘块的读写：
 
关闭debug为debug -f，之后在进行mkdir等操作不再显示i节点的相关操作和底层磁盘块的读写：
 
若debug指令参数不为-t /-f，报出错误：
 
4.23 修改密码设计 
4.23.1 程序说明
系统在开机时读取用户文件，用户输入用户名和密码后会在缓存中进行对比，如果存在用户名，且用户是当前登录用户，则可以进行修改。root用户可以修改所有人的密码。
4.23.2 实验结果
1.普通用户修改自己的密码：
 
若再以之前的密码登录，则无法登录：
 
若两次输入的密码不一致，报错：
 
若管理员尝试修改其他用户密码：
 
2.管理员修改普通用户密码：
 
4.24 help设计 
4.24.1 程序流程图
help指令很简单，就是打印一些系统指令信息。
4.24.2	程序说明
 
4.24.3 实验结果
 

4.25 用户列表展示及其root用户管理设计 
4.25.1 程序说明
系统在开机时读取用户文件，用户可以创建root用户，root用户拥有更多权限，比如可以查看用户列表，修改所有人的密码等。只有root用户可以使用查看用户列表功能，会将所有的用户输出到屏幕。

4.25.2 实验结果
管理员使用userlist查看：
 
若为普通用户，提示无权限：
 
4.26 更改管理员权限
4.26.1 程序说明
整个程序可以实现对于用户的管理员权限的申请功能。只需要在某一个用户登录之后，输入su，完成之后则可以进行了一些管理员操作。
4.26.2 实验结果
普通用户使用su指令赋予管理员权限：
 
4.27 查看磁盘空占用情况
4.27.1 程序说明
由于在设计底层过程中，实现了外存磁盘块的划分，并且在存储的时候，在特定位置存取了某一个磁盘块是否被占用，凭借此接口，则可以完成对于全部的磁盘块进行是否占用的判断。
4.27.2 实验结果
1.disklist -e [page] 输出空闲块列表，若不带参数，默认显示第1页
 
若页数小于0：
 
若页数大于上限：
 
2.disklist -f [page] 输出占用块列表，若不带参数，默认显示第1页
 
3.disklist -a [page] 输出所有块列表，若不带参数，默认显示第1页
 
4.28 删除指定用户
4.28.1 程序说明
对于管理员使用者，可以对于特定用户进行删除，而对于普通用户则没有此功能权限。
4.28.2 实验结果
管理员可以使用deluser [username]删除指定用户：
 
若普通用户尝试删除用户：
 
 
4.29 文本编辑器设计
4.29.1 程序流程图
 
 
4.26.2 程序说明
编辑器键盘输入使用windows系统调用实现。对于键盘区所有支持的键位，每30毫秒轮询windows键盘该键位状态消息。如果该键按下且未锁定，根据锁定该键后更新capsLock状态和shift状态，进行功能操作或者输出状态消息，在此步骤中会特判是否退出。如果该键未按下，则解锁该键键位。每次进行一次合法功能操作，清空控制台并且重新输出缓冲区。退出时会清空控制台。
4.26.3 实验结果
小写
 
CapsLock输入大写
 
Shift 输入符号并控制大小写
 
保存文件

 
放弃保存
 



5  结论
在完成课程设计的过程中，从系统架构设计，到实现基本功能、系统在开发板上可启动，再到逐渐添加文件系统、补充系统调用，最后整体功能完整测试、重构模块间接口……虽然经历了许多困难，但通过小组三人的精诚合作，最后都得到了圆满解决。在这次实践中，小组的所有成员都得到了宝贵的系统设计经验，并通过实践真正地领悟了操作系统各个模块的设计思想与实现细节，为以后在计算机学科进一步的探索打下了坚实的基础。
6  参考文献 
[1].	林果园 计算机操作系统 清华大学出版社.2021
[2].	邓飞，蔡波.基于Linux平台的文件系统设计研究[J].信息与电脑(理论版),2020,第32卷(20): 98-99
[3].	苏神保，刘丹.Linux下Ext3文件系统结构研究[J].智能计算机与应用,2019,第9卷(4): 304-306，312
[4].	Andrew S·Tanenbaum. 现代操作系统（第3版）.北京:机械工业出版社.2009.
 
7  收获、体会和建议
在这次操作系统课程设计的过程中，共有以下几点体会：
首先是对操作系统中文件管理系统整体框架的认识有了新的认识。尽管在一开始对文件管理的内部框架并不是很懂，但随着不断地查找资料和细读代码，逐渐了解了操作系统的整体构造情况。有了对操作系统的整体认识，便着手开始编写操作系统的代码，最终才一步步完成这次课设。
其次本次课设是分模块编写，每个人对于自己负责的模块有了更深的理解与认识，除此之外每位小组成员都需要不断提供接口给上层模块及服务，因此加强了小组成员之间的合作与沟通能力，并且对其他模块也有大概的认识。因此对于文件系统的上层，中层，底层，本小组都达到了一个实际文件系统的基本要求，对于操作系统的内核及框架，有了除课堂知识之外的新认知，这也是我们本次做这次课程设计的初衷，由于操作系统课设与考试时间过于靠近，并且课设时间较紧张，有一些功能没有全部完善，但在整体呈现上本次成果在本小组的认知下是非常符合要求且有很多扩展的，也感谢老师验收一天的辛苦，感谢老师如此负责。
最后，每个小组成员都付出了很多的时间与精力在自己负责的模块上，每个小组成员都很认真对待本次课程设计，所有的代码均为本组成员构建及编写，并没有面向开源文件系统进行修改，也并没使用任何库来编写，所以本次课设我们小组各个成员的工作量都符合本次要求，并可以很好的展现自己所负责的模块。
总而言之，本次课程设计增强了小组成员对操作系统的认知和理解，同时也更深地思考面向过程和面向对象之间巨大的差异。不过遗憾的是，这次课程设计的时间过分紧凑，倘若能宽裕些时间，我们相信最终成果会更加完善。