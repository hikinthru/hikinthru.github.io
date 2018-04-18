Most people today know what a "computer" is. But also consider it a "black box" that does invisible and magical things. It's really not that complicated. This is a brief introduction to how modern computers work.

## A Very Quick History of Computers
Technically a computer is simply anything that can take some information as an *input*, say a question like, "What is 3 plus 4," and provide an answer, or *output*, like "7". Believe it or not, the first use of the English term "computer" (as far back as the 1600's) referred to humans who could carry out calculations.

The earliest example of a mechanical computer that could be manipulated was the abacus, first found in the ancient civilization of Sumer 4,700 years ago. Leaping forward, the industrial age brought breakthroughs that would have long lasting impacts, from [Joseph Jacquard's looms](https://en.wikipedia.org/wiki/Jacquard_loom) which introduced the punch card as input, to Charles Babbage's [Difference Engine](https://en.wikipedia.org/wiki/Difference_engine), the first mechanical calculator.

In the mid nineteen hundreds great leaps were made with digital computers. In addition to amazing electrical engineering advances in the mechanics of computing, in 1937 [Claude Shannon](https://en.wikipedia.org/wiki/Claude_Shannon) proposed applying [Boolean logic](https://en.wikipedia.org/wiki/Boolean_algebra) and binary arithmetic to electrical circuits. And in 1945 [John Von Neumann](https://en.wikipedia.org/wiki/Von_Neumann_architecture) proposed an architectural framework for an electronic computer, on which modern computers are still based.

![Von-Neuman Computer Architecture](../images/Von_Neumann_Architecture.svg)  
The Von-Neuman Computer Architecture  
*[By Kapooht - Own work, CC BY-SA 3.0](https://commons.wikimedia.org/w/index.php?curid=25789639)*

In the forties, fifties and sixties computers were massive and measured by the number of rooms needed. While IBM would became the market leader in mainframes for decades, Thomas Watson, the son of IBM's founder, allegedly once said that there might be a world-wide market for five of them.

![An IBM 704 mainframe (1964)](../images/IBM_704_mainframe.gif)  

An IBM 704 mainframe (1964)  

*[Lawrence Livermore National Laboratory](https://commons.wikimedia.org/w/index.php?curid=1565787)*

By the 1970s and early 80s computer hardware had shrunk dramatically in size. A computer programming language named BASIC had been created, and IBM, Radio Shack and Apple entered the micro computer market. The dawn of the modern computer as we know it began.

![The Radioshack TRS-80 in 1977](../images/640px-Radioshack_TRS80-IMG_7206.jpg)  
The Radioshack TRS-80 in 1977  
*[By Rama & Musée Bolo - Own work, CC BY-SA 2.0 fr](https://commons.wikimedia.org/w/index.php?curid=37010666)*

## The Hardware Components
At its heart, as Von Neuman defined, a modern computer has four components: input, where the information or query goes in; the central processing unit, or CPU, where the calculations are done; memory, or the area that holds the information for the CPU to process; and output, where new information is sent. Most machines that we think of today as computers also have an additional component called "storage" (like a hard drive or a cloud space), where everything can live when the CPU is not thinking about it. That's it.

![The CPU](../images/cpu.png)  
*The modern computing paradigm*

An important point is that even if the device is as small as a smart phone or an iPod Nano, these functions, this paradigm of a modern computer, are still in it. It is notable today that the line between the general terms *memory* and *storage* are beginning to blur a bit with high-speed solid-state memory becoming able to function as both traditional random access memory (RAM) and long-term storage. But even so, the "functions" of RAM and storage are still two separate things, even if they occupy the same physical device.

To understand how it all works we'll start with the layers above the hardware, the software that runs it all.

## What is Software
Software is what you see when you turn on your computer, phone or tablet. Software provides all of the programming instructions (i.e., code) that control the computer and its components and give us the specific functionality that we use the device for.

Believe it or not software simply begins as text in a text editor. Anyone can use Notepad in Windows, TextEdit on a Mac, Gedit on Linux or even Nano in a Bash terminal to write a program. Today programmers can take advantage of more graphical interfaces like Microsoft's Visual Studio, but it isn't required. This code provides all of the instructions the computer (CPU) uses to do what we ask, as well as provide the interface for us to do the asking. Every bit of it begins by being written line by line by humans like you and I.

There are a few hundred different programming languages today, but the list of the most common is quite shorter. Windows, Linux and Android are all largely written in one or both of C and C++, Mac OSX is written in Objective C. Applications that run on computers most commonly use C++, Java, or Microsoft's .NET Framework of languages. Web applications are typically written in scripting and markup languages. Scripting languages commonly used are Python, PHP and JavaScript.

The difference between scripting and programming languages is that programming languages must be run through additional software called a compiler, so they are also known as *compiled languages*. A compiler translates the code written by the programmer into a lower-level version that the operating system can directly understand and communicate with. Scripting languages run as they are written and communicate with the operating system through an interpreter, so they are also known as *interpreted languages*. C, C++ and Java are compiled languages, Python, PHP and JavaScript are interpreted languages.

Software on today's desktop and laptop computers falls generally into two categories, the operating system, and the applications that we use for most of our computer tasks. There are other pieces that operate below applications such as drivers and programming interfaces, but for general purposes they can fall under the operating system (OS) layer.

## The Operating System and User Interface (UI)

![The Operating System Stack](../images/os-layers.png)

Every electronic device that qualifies as a modern computer requires programming code to control and manages its hardware. The hardware controlled on a personal computer includes the display devices, mouse, camera, sound, physical buttons, ports, etc. It also controls how applications running on the device access the CPU, memory and storage. The operating system provides a "layer" in the machine connecting the hardware with everything that can provide input to it, and everything to which it can provide output. The operating system is responsible for everything from the mundane "Close" button in the corner of an application window, to providing general navigation for using the machine (Windows' ubiquitous bottom left button to access programs and controls, or a smart phone's icons on the screen).

Applications live on top of the operating system, at the user's layer. To interact with the hardware an application must be written to work with the operating system. This is why some applications will run on one OS like Windows, but not another (like a Mac or Linux).

## The CPU


## Memory

## Storage

## Output