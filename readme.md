Let's get started...

Contents

1 Upgrade debian distribution to testing 1.1 Update distribution 1.2 Configure /etc/apt/sources.list 1.3 Upgrade distribution 2 Install ia32-libs 3 Enable unattended upgrades 4 Install emacs (for debian) 5 Install emacs (for ubuntu) 6 Install open ssh server 7 Install the Linux Standard Base (lsb) package 8 Install Mosh (mobile shell ssh replacement) 9 Install cmake 10 install python-dev 11 Install automake and autoconf 12 Install prerequisites 13 Customize message of the day 14 (Ubuntu Only) Shrink the verbose SSH welcome message 15 Set hostname (Ubuntu) 16 Randomize bash prompt color based on hostname 16.1 edit \~/.bashrc and set PS1 as follows: 16.2 Reload .bashrc 17 Upgrade to GCC-4.9 (for Mac OS X) 18 Upgrade to GCC-4.9 From Source (for linux) 18.1 configure gcc build: 18.2 build and install: 18.3 Update the gcc and g++ symbolic links 18.4 Test g++ 4.9 19 Install Clang 19.1 install prerequisites for LLDB 19.2 download and build clang 19.3 edit \~/.bashrc to add /usr/local/llvm-3.4/bin to your path and set CC and CXX accordingly: 19.4 Reload .bashrc 19.5 Edit /etc/sudoers as follows: 19.6 If you are using ubuntu, edit /etc/environment as follows: 19.7 Add the LLVM libraries by editing /etc/ld.so.conf.d/llvm.conf 20 Disable max\_align\_t when clang is being used: 21 Test clang 21.1 build and run: 22 Install gdb for getting a stacktrace from core dump 22.1 Test using gdb to print stacktraces from core dumps 22.2 How to programmatically enable core dumps from within your C++ program, and examine backtraces with LLDB 23 Install Clang static analysis tools 23.1 Test clang static analysis tools: 24 Install Intel® C++ Composer XE for Linux (64-bit target only) (optional) 24.1 Modify /etc/sudoers as follows: 24.2 If you are using ubuntu, edit /etc/environment as follows: 24.3 Add the Intel libraries by editing /etc/ld.so.conf.d/intel.conf 24.4 Test the Intel C++ compiler: 25 Install Intel® C++ Composer XE for Windows (64-bit target only) (optional) 25.1 Satisfy System requirements: 25.2 Set default configuration switches for running the Intel C++ Compiler under Windows 25.3 Test Intel C++ compiler: 26 Install zlib from source On Linux 27 Install openssl development library for Linux or Mac OS X 28 Install openssl development library for Windows 29 Install Boost 29.1 install ICU: 29.2 install zlib: 29.3 install libbz2 29.4 download boost source: 29.5 remove existing installation: 29.6 Build and install boost: 29.6.1 If you are using the Intel C++ Compiler, build and install libboost like so: 29.7 Build and install boost under Microsoft Windows: 29.8 Test boost: 30 How to patch boost::asio::ssl to support Ephemeral Diffie-Hellman (optional) 31 Build boost HTML documentation (optional) 32 Install Google sparsehash 33 Test Google Sparse Hash 34 Install the Eigen C++ linear algebra library 35 Test the Eigen C++ linear algebra library 35.1 Build and run eigen test program 36 Configure Intel Threading Building Blocks (this assumes you have installed the Intel C++ compiler) 36.1 resolve naming conflicts in /usr/include/tbb/internal/*flow*graph\_join\_impl.h and /usr/include/x86\_64-linux-gnu/bits/termios.h 36.2 Test Intel TBB: 37 Install ISPC (Intel SPMD Program Compiler) 37.1 Test Intel SPMD Program Compiler (ISPC) 38 Install SDL (Simple DirectMedia Layer) 38.1 Install SDL on Linux or Mac OS X 38.2 Install SDL On Windows 38.3 Test SDL: 38.3.1 Build and run test SDL program: 39 Install gcutil for Google Compute Engine 39.1 download gcutil https://code.google.com/p/google-compute-engine-tools/downloads/list 39.2 create a symbolic link to the gcutil binary 39.3 Authenticate to Google Compute Engine 39.4 specify a default project id: 40 Install gsutil for Google Cloud Storage 40.1 download gsutil 40.2 create a symbolic link to the gsutil binary 40.3 authenticate 40.4 copy objects to your bucket in parallel 41 Automatically chdir into your development directory upon login (optional): 42 Increase the maximum number of open file descriptors (optional): 43 Generate new host keys 44 Install cdecl for explaining C and C++ type declarations 45 Install libevent 45.1 Install libevent on Windows from cmd.exe: 45.2 Test libevent: 46 Install Boehm-Demers-Weiser conservative garbage collector 46.1 Test boehmgc 47 Configure Emacs 47.1 enable frame-fns 47.2 Install Yasnippet For Emacs 47.3 Install Emacs Autocomplete Mode 47.4 Install xcscope 47.5 Use Google's C++ Style 47.6 Enable Emacs Autopair Mode: 47.7 Enable "google this" functionality for emacs 47.8 Enable flymake mode with syntax error message display for C and C++ 47.9 Setup clang-format (automatically format C/C++) for use with emacs 48 Edit \~/.emacs to look this like: 49 Setup emacsclient to autospawn the emacs daemon (optional) 50 Synopsis of our customized emacs shortcuts 51 Optional add-ons to this C++ dev environment: 51.1 Setting up PNaCl C++ development environment on Linux 51.2 Setting up emscripten development environment on Linux

Upgrade debian distribution to testing

Update distribution

sudo apt-get update sudo apt-get upgrade sudo apt-get install zile Configure /etc/apt/sources.list

deb http://http.debian.net/debian testing main deb-src http://http.debian.net/debian testing main deb http://security.debian.org/ testing/updates main deb-src http://security.debian.org/ testing/updates main Upgrade distribution

sudo apt-get update sudo apt-get dist-upgrade sudo apt-get upgrade Install ia32-libs

sudo su dpkg --add-architecture i386 apt-get update apt-get install ia32-libs exit Enable unattended upgrades

sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get install -y unattended-upgrades Install emacs (for debian)

append emacs snapshot sources to /etc/apt/sources.list: deb http://emacs.naquadah.org/ stable/ deb-src http://emacs.naquadah.org/ stable/ add APT repositories to key ring: wget -q -O - http://emacs.naquadah.org/key.gpg | sudo apt-key add - update repositories: sudo apt-get update install emacs: sudo apt-get install emacs-snapshot-nox install emacs-goodies: sudo apt-get install emacs-goodies-el Install emacs (for ubuntu)

sudo add-apt-repository ppa:cassou/emacs

sudo apt-get purge emacs-snapshot-common emacs-snapshot-bin-common emacs-snapshot emacs-snapshot-el emacs-snapshot-gtk emacs23 emacs23-bin-common emacs23-common emacs23-el emacs23-nox emacs23-lucid auctex emacs24 emacs24-bin-common emacs24-common emacs24-common-non-dfsg

sudo apt-get update install emacs: sudo apt-get install emacs-snapshot-nox Install open ssh server

sudo apt-get install openssh-server Install the Linux Standard Base (lsb) package

sudo apt-get install lsb Install Mosh (mobile shell ssh replacement)

sudo apt-get install mosh Install cmake

sudo apt-get install cmake install python-dev

sudo apt-get install python-dev Install automake and autoconf

sudo apt-get install automake autoconf Install prerequisites

sudo apt-get install build-essential bzip2 lynx zile zlib1g-dev git unzip subversion Customize message of the day

sudo su chmod +w /etc/motd echo "" \> /etc/motd chmod -w /etc/motd exit (Ubuntu Only) Shrink the verbose SSH welcome message

sudo rm /etc/update-motd.d/51-cloudguest sudo rm /etc/update-motd.d/10-help-text sed -i '/.*add\_footnote.*/,/.*https.*/d' /usr/share/pyshared/landscape/sysinfo/landscapelink.py Set hostname (Ubuntu)

sudo su echo "dev" \> /etc/hostname hostname dev Randomize bash prompt color based on hostname

edit \~/.bashrc and set PS1 as follows:

hostnamecolor=\$(hostname | od | tr ' ' '' | awk '{total = total + \(1}END{print 30 + (total % 6)}') if [ \)hostnamecolor = 30 ]; then hostnamecolor=31 fi export PS1='[33[01;\${hostnamecolor}m]\$[33[00m] ' Reload .bashrc

. \~/.bashrc Upgrade to GCC-4.9 (for Mac OS X)

sudo port install gcc49 sudo port select gcc mp-gcc49 sudo port select --list gcc Upgrade to GCC-4.9 From Source (for linux)

NOTE: If you have followed the instructions on this page so far, you should already have an older version of gcc installed at this point. We will be upgrading to the latest version of GCC so that we can use C++14 Install prerequisites on Linux: sudo apt-get install libgmp3-dev libgmp-dev libmpfr-dev libmpc-dev flex bison libc6-dev gcc-multilib Download source and build: sudo mkdir /gcc sudo chmod 777 /gcc svn co svn://gcc.gnu.org/svn/gcc/trunk /gcc

cd /gcc ./contrib/download\_prerequisites

mkdir /gcc/objdir cd /gcc/objdir configure gcc build:

View configuration flags used to build the distro version of gcc: gcc -v Customize this command accordingly: For Linux: ../configure -v --enable-languages=c,c++,go --prefix=/usr --program-suffix=-4.9 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --libdir=/usr/lib --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-time=yes --enable-gnu-unique-object --enable-plugin --with-system-zlib --disable-ppl-version-check --disable-multilib --enable-checking=release --build=x86\_64-linux-gnu --host=x86\_64-linux-gnu --target=x86\_64-linux-gnu build and install:

sudo ln -s /usr/include/x86\_64-linux-gnu/zconf.h /usr/include sudo ln -s /usr/lib/x86\_64-linux-gnu /usr/lib64

grep -c \^processor /proc/cpuinfo | xargs -I '{}' make -j '{}'

sudo make install Update the gcc and g++ symbolic links

sudo rm /usr/bin/g++ sudo ln -s /usr/bin/g++-4.9 /usr/bin/g++

sudo rm /usr/bin/gcc sudo ln -s /usr/bin/gcc-4.9 /usr/bin/gcc

sudo rm /usr/bin/cpp sudo ln -s /usr/bin/cpp-4.9 /usr/bin/cpp

sudo rm /usr/bin/gcov sudo ln -s /usr/bin/gcov-4.9 /usr/bin/gcov

sudo rm /usr/bin/c++ sudo ln -s /usr/bin/c++-4.9 /usr/bin/c++ Test g++ 4.9

Edit /tmp/generalized-lambda.cpp: \#include <iostream> \#include <algorithm>

void f(std::size\_t);

int main() { int x = 4; auto y = [&r = x, x = x+1]()-\>int { r += 2; return x+2; }(); // Updates ::x to 6, and initializes y to 7.

std::cout \<\< y \<\< std::endl;

int input; std::cin \>\> input;

f(input);

return 0; }

void f(std::size\_t n) { int a[n]; for (std::size\_t i = 0; i \< n; ++i) a[i] = 2\*i; std::sort(a, a+n);

for( int i = 0; i \< n; i++) { std::cout \<\< a[i] \<\< " "; } std::cout \<\< std::endl; } Build and run: cd /tmp; g++-4.9 -std=c++1y generalized-lambda.cpp; ./a.out Verify which libraries we are linking against: ldd a.out Install Clang

install prerequisites for LLDB

NOTE: LLDB is optional sudo apt-get install swig libreadline-dev libeditline-dev libedit-dev download and build clang

sudo mkdir /llvm sudo chmod 777 /llvm cd /llvm svn co http://llvm.org/svn/llvm-project/llvm/trunk llvm

cd llvm/tools/ svn co http://llvm.org/svn/llvm-project/cfe/trunk clang svn co http://llvm.org/svn/llvm-project/lldb/trunk lldb cd ../.. cd llvm/tools/clang/tools svn co http://llvm.org/svn/llvm-project/clang-tools-extra/trunk extra cd ../../../.. cd llvm/projects svn co http://llvm.org/svn/llvm-project/compiler-rt/trunk compiler-rt cd ../.. mkdir build Build clang/llvm on Linux: cd /llvm/build ../llvm/configure --prefix=/usr/local/llvm-3.4 --bindir=/usr/local/llvm-3.4/bin --enable-cxx11 --enable-optimized CXX=/usr/bin/g++-4.9 CC=/usr/bin/gcc-4.9

grep -c \^processor /proc/cpuinfo | xargs -I '{}' make -j '{}'

sudo make install Build clang/llvm on Mac OS X: sudo port install swig swig-python

cd /llvm/build ../llvm/configure --prefix=/usr/local/llvm-3.4 --bindir=/usr/local/llvm-3.4/bin --enable-cxx11 --enable-optimized CXX=/opt/local/bin/g++ CC=/opt/local/bin/gcc

sysctl hw.ncpu | awk '{print \$2}' | xargs -I '{}' make -j '{}'

sudo cp /llvm/build/Release+Asserts/bin/clang-format /usr/bin/

sudo make install edit \~/.bashrc to add /usr/local/llvm-3.4/bin to your path and set CC and CXX accordingly:

PATH=\$PATH:/usr/local/llvm-3.4/bin

export CC=/usr/local/llvm-3.4/bin/clang export CXX=/usr/local/llvm-3.4/bin/clang++ Reload .bashrc

. \~/.bashrc Edit /etc/sudoers as follows:

sudo su chmod +w /etc/sudoers sed -i 's@:/bin"@:/bin:/usr/local/llvm-3.4/bin"@' /etc/sudoers chmod -w /etc/sudoers exit If you are using ubuntu, edit /etc/environment as follows:

sudo emacs /etc/environment Edit /etc/environment: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/usr/local/llvm-3.4/bin" export CC=/usr/local/llvm-3.4/bin/clang export CXX=/usr/local/llvm-3.4/bin/clang++ Add the LLVM libraries by editing /etc/ld.so.conf.d/llvm.conf

sudo emacs /etc/ld.so.conf.d/llvm.conf add this line: /usr/local/llvm-3.4/lib Apply the new settings: sudo rm /usr/lib/x86\_64-linux-gnu/libstdc++.so.6.0.19-gdb.py sudo ldconfig Confirm the new settings: sudo ldconfig -p | grep -i llvm NOTE: If you don't do this, you may get the following error later on: error running timer \`ac-update-greedy': (error "Process clang-complete not running") Disable max\_align\_t when clang is being used:

sudo sed -i 's/.*max\_align\_t.*/\#ifndef **clang**&\#endif/' /usr/lib/gcc/x86\_64-linux-gnu/4.9.0/../../../../include/c++/4.9.0/cstddef NOTE: If you don't do this, you will get the following error when compiling with clang on a dev environment using gcc-4.9: /usr/lib/gcc/x86\_64-linux-gnu/4.9.0/../../../../include/c++/4.9.0/cstddef:52:11: error: no member named 'max\_align\_t' in the global namespace using ::max\_align\_t; \~\~\^ 1 error generated. Test clang

edit /tmp/thread.cpp: \#include <iostream> \#include <thread>

thread\_local int i=0;

void f(int newval){ i=newval; }

void g(){ std::cout\<<i;
}

void threadfunc(int id){
  f(id);
  ++i;
  g();
}

int main(){
  i=9;
  std::thread t1(threadfunc,1);
  std::thread t2(threadfunc,2);
  std::thread t3(threadfunc,3);

  t1.join();
  t2.join();
  t3.join();
  std::cout<<i<<std::endl;
}
build and run:

cd /tmp
clang++ -std=c++1y -fsanitize=memory -fno-omit-frame-pointer -O1 -g -fno-optimize-sibling-calls -pthread thread.cpp
/tmp/a.out
NOTE: On OS X, compile and run like this:
clang++ -std=c++1y -stdlib=libc++  -fno-omit-frame-pointer -O1 -g -fno-optimize-sibling-calls -pthread thread.cpp
./a.out
Install gdb for getting a stacktrace from core dump

sudo apt-get install gdb
Test using gdb to print stacktraces from core dumps

edit /tmp/badcode.cpp:
int main()
{
  int *p = nullptr;
  *p = 0;
  return 0;
}
compile:
cd /tmp
g++ -g -Wall -std=c++1y -pedantic -O0 -Werror -Wextra badcode.cpp -o badcode.bin
set the core file size:
ulimit -c unlimited
Generate a segmentation fault so that we can use gdb to analyze the coredump:
cd /tmp
./badcode.bin
Run gdb:
cd /tmp
gdb /tmp/badcode.bin /tmp/core
Then, use one of the following from inside gdb:
(gdb) bt
(gdb) bt full
(gdb) info threads
(gdb) thread apply all bt
(gdb) thread apply all bt full
How to programmatically enable core dumps from within your C++ program, and examine backtraces with LLDB

edit /tmp/badcode2.cpp:
#include <sys/resource.h> \#include <stdio.h> \#include <stdlib.h> /\* exit, EXIT\_FAILURE \*/ \#include <errno.h> \#include <string.h>

void enableCoreDumps() { struct rlimit core\_limit; core\_limit.rlim\_cur = RLIM\_INFINITY; core\_limit.rlim\_max = RLIM\_INFINITY;

if (setrlimit(RLIMIT\_CORE, &core\_limit) \< 0) { fprintf( stderr, "setrlimit: %s: core dumps may be truncated or non-existant", strerror(errno)); exit(EXIT\_FAILURE); } }

int main() { enableCoreDumps();

int *p = nullptr; *p = 0; return 0; } compile: cd /tmp clang++ -c -g -Wall -std=c++1y -pedantic -O0 -Werror -Wextra badcode2.cpp -o badcode2.o clang++ badcode2.o -o badcode2.bin Generate a segmentation fault so that we can use LLDB to analyze the coredump: cd /tmp ./badcode2.bin Run LLDB: cd /tmp lldb ./badcode2.bin --core ./core Then, use one of the following from inside LLDB: (lldb) thread backtrace (lldb) bt (lldb) thread backtrace all (lldb) bt all (lldb) thread apply all bt full Install Clang static analysis tools

sudo cp -Ra /llvm/llvm/tools/clang/tools/scan-view/\* /usr/local/llvm-3.4/bin/ sudo cp -Ra /llvm/llvm/tools/clang/tools/scan-build/\* /usr/local/llvm-3.4/bin/ Test clang static analysis tools:

cd /YOUR-PROJECTS-ROOT-DIRECTORY mkdir bin cd bin cmake .. clang-build make -j 32 Or: scan-build gcc -c mycode.c mycode2.c Install Intel® C++ Composer XE for Linux (64-bit target only) (optional)

Install Java: sudo apt-get install openjdk-7-jdk openjdk-7-jre-headless Download icc: From where can I download the Intel C++ compiler? https://registrationcenter.intel.com https://premier.intel.com sudo mkdir /tmp/intel-icc-v13 sudo chmod 777 /tmp/intel-icc-v13 cd /tmp/intel-icc-v13

wget '<THE DOWNLOAD URL YOU WERE PROVIDED WITH WHEN YOU REGISTERED FOR INTEL C++ Compiler>' tar -xzvf l\_ccompxe\_intel64\_2013.5.192.tgz Run installation: cd /tmp/intel-icc-v13/l\_ccompxe\_intel64\_2013.5.192/ sudo ./install.sh When prompted, enter your serial number. Append the following line to \~/.bashrc: source /opt/intel/composer\_xe\_2013/bin/compilervars.sh intel64 Cleanup: sudo rm -rf /tmp/intel-icc-v13/ Modify /etc/sudoers as follows:

sudo su chmod +w /etc/sudoers sed -i 's@/bin"@/bin:/opt/intel/bin"@' /etc/sudoers chmod -w /etc/sudoers exit If you are using ubuntu, edit /etc/environment as follows:

sudo emacs /etc/environment Edit /etc/environment: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/usr/local/llvm-3.4/bin:/opt/intel/bin" Add the Intel libraries by editing /etc/ld.so.conf.d/intel.conf

sudo emacs /etc/ld.so.conf.d/intel.conf add these lines to /etc/ld.so.conf.d/intel.conf: /opt/intel/lib/mic /opt/intel/lib/intel64 Apply the new settings: sudo ldconfig Confirm the new settings (check for location of cilk plus library): sudo ldconfig -p | grep -i cilk Test the Intel C++ compiler:

edit /tmp/variadic-template-function.cpp: \#include <iostream> using namespace std;

void func() { cerr \<\< "EMPTY" \<\< endl; }

template <class A, class... B> void func(A argHead, B... argTail) { cerr \<\< "A: " \<\< argHead \<\< endl; func(argTail...); }

int main(void) { func(1, 2, 3, 4, 5, 6); return 0; } Build and run on Linux: cd /tmp

icpc -std=c++11 -gcc-name=/usr/bin/gcc-4.7 -gxx-name=/usr/bin/g++-4.7 -I/usr/include/x86\_64-linux-gnu/c++/4.7 variadic-template-function.cpp -o variadic-template-function-test

./variadic-template-function-test Install Intel® C++ Composer XE for Windows (64-bit target only) (optional)

Satisfy System requirements:

Install Microsoft Visual C++ Express 2012 for Windows Desktop Download and install Intel® C++ Composer XE for Windows (64-bit target only) Set default configuration switches for running the Intel C++ Compiler under Windows

Edit C:Files (x86)XE 201364.cfg to look like this: \# This Configuration file may be used for additional switches /Qlocation,link,"C:Files (x86)Visual Studio 11.0.exe" Test Intel C++ compiler:

edit /tmp/variadic-template-function.cpp: \#include <iostream> using namespace std;

void func() { cerr \<\< "EMPTY" \<\< endl; }

template <class A, class... B> void func(A argHead, B... argTail) { cerr \<\< "A: " \<\< argHead \<\< endl; func(argTail...); }

int main(void) { func(1, 2, 3, 4, 5, 6); return 0; } Build and run on Windows with the Intel C++ Compiler: Open a command prompt preconfigured with intel compiler environment variables: "Intel 64 Visual Studio 2012 mode"

Compile the example program: "\$ icl /Qstd=c++11 variadic-template-function.cpp -o variadic-template-function-test.exe"

Execute the compiled program: "\$ ./variadic-template-fucntion-test.exe" Install zlib from source On Linux

sudo mkdir /zlib sudo chmod 777 /zlib cd /tmp wget 'http://zlib.net/zlib-1.2.8.tar.gz' tar -xzvf zlib-1.2.8.tar.gz mv zlib-1.2.8/\* /zlib/ cd /zlib ./configure --prefix=/usr make sudo make install Install openssl development library for Linux or Mac OS X

Find the latest version at: ftp://ftp.openssl.org/snapshot cd /tmp wget 'ftp://ftp.openssl.org/snapshot/openssl-SNAP-<LATESTVERSION>.tar.gz' tar -xzvf openssl-*.tar.gz cd /tmp/openssl-SNAP* Build on Linux: ./config --prefix=/usr threads zlib no-shared -fPIC make depend make sudo make install Build on OS X: ./Configure darwin64-x86\_64-cc --prefix=/opt/local make depend make sudo make install Install openssl development library for Windows

Install the Netwide Assembler (NASM) from: http://sourceforge.net/projects/nasm/ Add the following to the windows system PATH variable: C:Files (x86)Install ActivePerl for Windows 64-bit from: http://www.activestate.com/activeperl/downloads From cygwin: cd /tmp wget 'ftp://ftp.openssl.org/source/openssl-1.0.1e.tar.gz' tar -xzvf openssl-*.tar.gz cd /tmp/openssl* mkdir /cygdrive/c/libssl mv ./\* /cygdrive/c/libssl/ From cmd.exe: cd c:perl Configure VC-WIN64A --prefix=c:perl util.pl crypto ssl update ms\_win64a nmake -f ms.mak nmake -f ms.mak install The openssl libraries and header files are now at: c:Install Boost

install ICU:

sudo apt-get install libicu-dev libicu48 install zlib:

sudo apt-get install zlib1g zlib1g-dev install libbz2

sudo apt-get install libbz2-dev libbz2-1.0 download boost source:

If you want to use the current release of the Boost C++ libraries, do this: sudo mkdir /libboost sudo chmod 777 /libboost/ cd /libboost/ wget 'http://sourceforge.net/projects/boost/files/boost/1.54.0/boost\_1\_54\_0.tar.gz/download' -O boost\_1\_54.tar.gz tar -xzvf boost\_1\_54.tar.gz cd boost\_1\_54\_0 If you want to build from the current Boost development code, do this: For further information on the boost SVN repository, read this: https://svn.boost.org/trac/boost/wiki/BoostSubversion sudo mkdir /libboost sudo chmod 777 /libboost/ cd /libboost/ svn co http://svn.boost.org/svn/boost/trunk boost-trunk

cd boost-trunk remove existing installation:

sudo apt-get --purge remove libboost1.53-dev libboost1.53-doc libboost1.53-all-dev sudo apt-get --purge remove libboost1.49-dev libboost1.49-doc libboost1.49-all-dev libboost-python1.49.0 sudo apt-get --purge remove libboost-dev libboost-doc sudo rm -rf /usr/include/boost sudo rm -rf /usr/include/boost* sudo rm -rf /usr/lib/libboost* Build and install boost:

On Linux with GCC (with segmented stacks, which are supported only on Linux): Compile boost with GCC On Linux: note: 'Boost.Coroutine supports usage of a segemented-stack, e. g. the size of the stack of a coroutine grows on demand. The coroutine is created with a stack with an minimal stack and if the coroutine is execute the stack size is increased as required. We are using segmented stacks to benefit from golang-like functionality in C++ segmented-stacks are not supported by clang, only by gcc: (see: http://www.boost.org/doc/libs/1\_54\_0/libs/coroutine/doc/html/coroutine/stack/segmented\_stack.html) ./b2 --clean-all ./bootstrap.sh --with-toolset=gcc --with-libraries=all --prefix=/usr grep -c \^processor /proc/cpuinfo | xargs -I '{}' ./b2 --prefix=/usr toolset=gcc cxxflags="-std=c++11" threading=multi segmented-stacks=on link=static -j '{}' sudo ./b2 --prefix=/usr toolset=gcc cxxflags="-std=c++11" threading=multi segmented-stacks=on link=static install On Mac OS X With GCC: For Mac OS X, install and activate gcc 4.7 prior to building: sudo port install gcc49 sudo port select gcc mp-gcc49 sudo port select --list gcc Download zlib: sudo mkdir /zlib sudo chmod 777 /zlib cd /tmp wget 'http://zlib.net/zlib-1.2.8.tar.gz' tar -xzvf zlib-1.2.8.tar.gz mv zlib-1.2.8/\* /zlib/ cd /zlib ./configure make sudo make install Build and install boost with gcc for Mac OS X: NOTE: segmented stacks are not supported by gcc on OS X. ./b2 --clean-all ./bootstrap.sh --with-toolset=gcc --with-libraries=all --prefix=/usr sysctl hw.ncpu | awk '{print \$2}' | xargs -I '{}' ./b2 --prefix=/usr toolset=gcc cxxflags="-std=c++11" threading=multi link=static -sZLIB\_SOURCE=/zlib -j '{}' sudo ./b2 --prefix=/usr toolset=gcc cxxflags="-std=c++11" threading=multi link=static -sZLIB\_SOURCE=/zlib install On Linux with clang: ./b2 --clean-all ./bootstrap.sh --with-toolset=clang --with-libraries=all --prefix=/usr grep -c \^processor /proc/cpuinfo | xargs -I '{}' ./b2 --prefix=/usr toolset=clang cxxflags="-std=c++1y" threading=multi link=static -j '{}' sudo ./b2 --prefix=/usr toolset=clang cxxflags="-std=c++1y" threading=multi link=static install On Mac OS X with clang: ./b2 --clean-all ./bootstrap.sh --with-toolset=clang --with-libraries=all --prefix=/usr sysctl hw.ncpu | awk '{print \$2}' | xargs -I '{}' ./b2 --prefix=/usr toolset=clang cxxflags="-std=c++11 -stdlib=libc++" threading=multi link=static --without-signals -j '{}' sudo ./b2 --prefix=/usr toolset=clang cxxflags="-std=c++11 -stdlib=libc++" threading=multi link=static --without-signals install If you are using the Intel C++ Compiler, build and install libboost like so:

NOTE: It is possible to build boost with clang and then to link boost into programs which are built with the Intel C++ compiler. For instance, you can develop a Cilk Plus or TBB application using the Intel C++ Compiler and then link against boost libraries which were built with clang, such as boost\_system. This mixed compiler approach may allow you to incorporate libraries which cannot yet be built with the Intel C++ Compiler into applications which are targeting the Intel C++ platform (Cilk Plus, TBB, MKL, Intel Concurrent Collections For C++, AVX2, etc...) ./b2 --clean-all ./bootstrap.sh --with-toolset=intel-linux --with-libraries=all --prefix=/usr

grep -c \^processor /proc/cpuinfo | xargs -I '{}' ./b2 --prefix=/usr toolset=intel-linux cxxflags="-std=c++11 -gcc-name=/usr/bin/gcc-4.7 -gxx-name=/usr/bin/g++-4.7 -I/usr/include/x86\_64-linux-gnu/c++/4.7" threading=multi link=static -j '{}'

sudo ./b2 --prefix=/usr toolset=intel-linux cxxflags="-std=c++11 -gcc-name=/usr/bin/gcc-4.7 -gxx-name=/usr/bin/g++-4.7 -I/usr/include/x86\_64-linux-gnu/c++/4.7" threading=multi link=static install Build and install boost under Microsoft Windows:

Download boost source using cygwin: mkdir /cygdrive/c/libboost cd /cygdrive/c/libboost svn co http://svn.boost.org/svn/boost/trunk boost-trunk exit Download bzip2 source using cygwin: mkdir /cygdrive/c/bzip2 cd /cygdrive/c/bzip2 wget "http://www.bzip.org/1.0.6/bzip2-1.0.6.tar.gz" tar -xzvf bzip2-1.0.6.tar.gz cp bzip2-1.0.6/\* . exit Download zlib source using cygwin: mkdir /cygdrive/c/zlib cd /cygdrive/c/zlib wget 'http://zlib.net/zlib-1.2.8.tar.gz' tar -xzvf zlib-1.2.8.tar.gz cp zlib-1.2.8/\* . exit Download ICU: mkdir /cygdrive/c/icu cd /cygdrice/c/icu wget': wget 'http://download.icu-project.org/files/icu4c/51.2/icu4c-51\_2-Win64-msvc10.zip unzip unzip': unzip icu4c-51\_2-Win64-msvc10.zip mv icu/\* . cd /cygdrive/c/icu/icu/lib64 cp icuuc.lib icuucd.lib cp icuin.lib icuind.lib Run cmd.exe (not Cygwin), and build the boost libraries using Microsoft's VC++ compiler: cd c:-trunk b2.exe --clean-all bootstrap.bat b2.exe -sZLIB\_SOURCE=c:-sBZIP2\_SOURCE=c:2 -sICU\_PATH=c:threading=multi link=static variant=release runtime-link=static --layout=tagged address-model=64 -j8 b2.exe -sZLIB\_SOURCE=c:-sBZIP2\_SOURCE=c:2 -sICU\_PATH=c:threading=multi link=static variant=release runtime-link=static --layout=tagged address-model=64 -j8 install Test boost:

edit /tmp/regex.cpp: \#include <boost/regex.hpp> \#include <iostream> \#include <string>

int main() { std::string line; boost::regex pat("\^Subject: (Re: |Aw: )*(.*)");

while (std::cin) { std::getline(std::cin, line); boost::smatch matches; if (boost::regex\_search(line, matches, pat)) { std::cout \<\< matches[2] \<\< std::endl; } else { std::cout \<\< "NO MATCH: " \<\< matches[0] \<\< std::endl; } } } On Linux, build and run with gcc: cd /tmp g++ -std=c++11 regex.cpp -lboost\_regex -o regex ./a.out On Linux, build and run with clang: cd /tmp clang++ -std=c++1y regex.cpp -lboost\_regex -o regex ./a.out On Linux, build and run with the Intel C++ compiler: cd /tmp icpc -std=c++11 -gcc-name=/usr/bin/gcc-4.7 -gxx-name=/usr/bin/g++-4.7 -I/usr/include/x86\_64-linux-gnu/c++/4.7 regex.cpp -o regex -lboost\_regex ./regex On Mac OS X, compile and link with Clang as follows: cd /tmp clang++ -std=c++11 regex.cpp -stdlib=libc++ -lboost\_regex -o regex ./regex On Windows, compile and link with the Intel C++ Compiler: NOTE: If you are using cmake, you can disable boost auto-linking with ADD\_DEFINITIONS("-DBOOST\_ALL\_NO\_LIB") icl /Qstd=c++11 c:-programs.cpp -Ic:-DBOOST\_ALL\_NO\_LIB c:\_regex-mt-s.lib How to patch boost::asio::ssl to support Ephemeral Diffie-Hellman (optional)

Insert the following code snippet as a public member function to class context in file /usr/include/boost/asio/ssl/context.hpp: BOOST\_ASIO\_DECL void set\_cipher\_suites(const std::string& ciphers) { OpenSSL\_add\_all\_algorithms(); OpenSSL\_add\_all\_ciphers(); OpenSSL\_add\_all\_digests();

    ::SSL_CTX_set_options(
        handle_, SSL_OP_SINGLE_ECDH_USE | SSL_OP_SINGLE_DH_USE | SSL_OP_ALL |
                     SSL_OP_NO_SSLv2 | SSL_OP_CIPHER_SERVER_PREFERENCE);
    ::SSL_CTX_set_ecdh_auto(handle_, 1);
    ::SSL_CTX_set_cipher_list(handle_, ciphers.c_str());

} You can now specify cipher suites from code that uses boost::asio::ssl like so: auto sslcontext\_(boost::asio::ssl::context::sslv23\_server);

    sslcontext_.use_private_key(boost::asio::buffer(private_key_file),
                                boost::asio::ssl::context::pem);
    sslcontext_.use_certificate_chain(
        boost::asio::buffer(certificate_chain_file));
    sslcontext_.use_tmp_dh(boost::asio::buffer(tmp_dh4096)); /// copied from the 'dh4096.pem' file in the '/apps' directory of the openssl source tarball

    sslcontext_.set_cipher_suites(
        "TLS_DHE_RSA_WITH_AES_256_GCM_SHA384:TLS_DHE_RSA_WITH_AES_128_GCM_"
        "SHA256:TLS_DHE_RSA_WITH_CAMELLIA_256_CBC_SHA:TLS_DHE_RSA_WITH_AES_256_"
        "CBC_SHA256:TLS_DHE_RSA_WITH_AES_256_CBC_SHA:"
        "TLS_ECDHE_RSA_WITH_RC4_128_SHA:TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA:TLS_"
        "ECDHE_RSA_WITH_AES_256_CBC_SHA:TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA:"
        "ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-RC4-SHA:ECDHE-RSA-AES128-SHA256:"
        "ECDHE-RSA-AES256-SHA:EECDH:kEECDH:ECDH:kEDH:"
        // comment out the following two lines if you only want to support perfect-forwarding:
        "RC4-SHA"
        ":HIGH:AES128-GCM-SHA256:"
        "!ADH:!NULL:!MD5:!SSLv2:!aNULL:!LOW");

} Build boost HTML documentation (optional)

sudo apt-get install xsltproc sudo apt-get install doxygen sudo apt-get install curl

sudo mkdir /boostdoc sudo chmod 777 /boostdoc

cd /boostdoc chmod +x /libboost/boost-trunk/tools/boostbook/setup\_boostbook.sh

BOOST\_ROOT=/libboost/boost-trunk /libboost/boost-trunk/tools/boostbook/setup\_boostbook.sh To generate html documentation for a particular boost library, do so from that library's doc subdirectory: cd /libboost/boost-trunk/libs/coroutine/doc ../../../b2 --v2 format=html variant=release

cd /libboost/boost-trunk/libs/asio/doc ../../../b2 --v2 format=html variant=release You may then view the html documentation at: /libboost/boost-trunk/libs/coroutine/doc/html /libboost/boost-trunk/libs/asio/doc/html Install Google sparsehash

On Linux: sudo mkdir /libgoogle-sparse-hash sudo chmod 777 /libgoogle-sparse-hash cd /

svn checkout http://sparsehash.googlecode.com/svn/trunk/ /libgoogle-sparse-hash cd /libgoogle-sparse-hash

./configure --prefix=/usr CXX=clang++ CC=clang CXXFLAGS="-std=c++1y" grep -c \^processor /proc/cpuinfo | xargs -I '{}' make -j '{}' sudo make install On OSX: sudo mkdir /libgoogle-sparse-hash sudo chmod 777 /libgoogle-sparse-hash cd /

svn checkout http://sparsehash.googlecode.com/svn/trunk/ /libgoogle-sparse-hash cd /libgoogle-sparse-hash

./configure --prefix=/usr CXX=g++ CC=gcc CXXFLAGS="-std=c++1y" make sudo make install On Windows: Under cygwin.exe: mkdir /cygdrive/c/libgoogle-sparse-hash cd /cygdrive/c

svn checkout http://sparsehash.googlecode.com/svn/trunk/ libgoogle-sparse-hash Test Google Sparse Hash

edit /tmp/google-sparse-hash.cpp: \#include <google/sparse_hash_map> \#include <iostream>

using std::hash;

struct eqstr { bool operator()(const char\* s1, const char\* s2) const { return (s1 == s2) || (s1 && s2 && strcmp(s1, s2) == 0); } };

int main() { google::sparse\_hash\_map<const char*, int, hash<const char*>, eqstr\> months;

months.set\_deleted\_key(NULL); months["january"] = 31; months["february"] = 28; months["march"] = 31; months["april"] = 30; months["may"] = 31; months["june"] = 30; months["july"] = 31; months["august"] = 31; months["september"] = 30; months["october"] = 31; months["november"] = 30; months["december"] = 31;

std::cout \<\< "september -\> " \<\< months["september"] \<\< std::endl; std::cout \<\< "april -\> " \<\< months["april"] \<\< std::endl; std::cout \<\< "june -\> " \<\< months["june"] \<\< std::endl; std::cout \<\< "november -\> " \<\< months["november"] \<\< std::endl;

return 0; } build and run with clang: cd /tmp clang++ -std=c++1y google-sparse-hash.cpp ./a.out build and run with clang on OSX: cd /tmp clang++ -std=c++1y -stdlib=libc++ google-sparse-hash.cpp ./a.out build and run with gcc: cd /tmp g++ -std=c++1y google-sparse-hash.cpp ./a.out build and run with the Intel C++ Compiler on Linux: cd /tmp icpc -std=c++11 -gcc-name=/usr/bin/gcc-4.7 -gxx-name=/usr/bin/g++-4.7 -I/usr/include/x86\_64-linux-gnu/c++/4.7 google-sparse-hash.cpp ./a.out build and run with the Intel C++ Compiler on Mac OS X: cd /tmp icpc -std=c++11 -gcc-name=/opt/local/bin/gcc-mp-4.6 -gxx-name=/opt/local/bin/g++-mp-4.6 -I/opt/local/include/gcc46/c++ google-sparse-hash.cpp ./a.out build and run with the Intel C++ Compiler on Windows: cd /tmp icl /Qstd=c++11 -Ic:-sparse-hash-Ic:-sparse-hashgoogle-sparse-hash.cpp google-sparse-hash.exe Install the Eigen C++ linear algebra library

Eigen is a header-only library; the headers are platform independent. Therefore, the only configuration necessary is to copy the headers to the appropriate destination: Install under Linux or Mac OS X: cd /tmp wget --no-check-certificate 'http://bitbucket.org/eigen/eigen/get/3.2.0.tar.gz' tar -xzvf 3.2.0.tar.gz sudo mkdir /libeigen sudo chmod 777 /libeigen

cp -Ra eigen-eigen-ffa86ffb5570/Eigen/\* /libeigen/ cp -Ra eigen-eigen-ffa86ffb5570/unsupported/Eigen/\* /libeigen/

sudo cp -Ra /libeigen /usr/include/Eigen Install under Windows: Under cygwin: mkdir -p /cygdrive/c/libeigen/Eigen cd /tmp wget --no-check-certificate 'http://bitbucket.org/eigen/eigen/get/3.2.0.tar.gz' tar -xzvf 3.2.0.tar.gz cp -Ra eigen-eigen-ffa86ffb5570/Eigen /cygdrive/c/libeigen cp -Ra eigen-eigen-ffa86ffb5570/unsupported /cygdrive/c/libeigen Test the Eigen C++ linear algebra library

Edit /tmp/eigen-test.cpp: \#include <iostream> \#include <Eigen/Dense>

using Eigen::MatrixXd;

int main() { MatrixXd m(2,2); m(0,0) = 3; m(1,0) = 2.5; m(0,1) = -1; m(1,1) = m(1,0) + m(0,1); std::cout \<\< m \<\< std::endl;

return 0; } Build and run eigen test program

On Linux with clang: clang++ -std=c++1y -Wall -Wextra -O0 -g -m64 -DEIGEN\_NO\_DEBUG eigen-test.cpp -o eigen-test ./eigen-test On Linux with gcc: g++ -std=c++1y -Wall -Wextra -O0 -g -m64 -DEIGEN\_NO\_DEBUG eigen-test.cpp -o eigen-test ./eigen-test On OS X: clang++ -std=c++1y -Wall -Wextra -O0 -g -m64 -DEIGEN\_NO\_DEBUG -stdlib=libc++ eigen-test.cpp -o eigen-test ./eigen-test On Linux with the Intel C++ Compiler: icpc -std=c++11 -gcc-name=/usr/bin/gcc-4.7 -gxx-name=/usr/bin/g++-4.7 -I/usr/include/x86\_64-linux-gnu/c++/4.7 eigen-test.cpp -o eigen-test ./eigen-test On OS X with Intel C++ Compiler: icpc -std=c++11 -gcc-name=/opt/local/bin/gcc-mp-4.6 -gxx-name=/opt/local/bin/g++-mp-4.6 -I/opt/local/include/gcc46/c++ eigen-test.cpp -o eigen-test ./eigen-test On Windows with Intel C++ Compiler: icl /Qstd=c++11 -Ic: -Ic:eigen.cpp eigen.exe Configure Intel Threading Building Blocks (this assumes you have installed the Intel C++ compiler)

resolve naming conflicts in /usr/include/tbb/internal/*flow*graph\_join\_impl.h and /usr/include/x86\_64-linux-gnu/bits/termios.h

On Linux: cat /opt/intel/composer\_xe\_2013/tbb/include/tbb/internal/*flow*graph\_join\_impl.h | perl -pe 's/(B[0-9]{1,1})/ B\$1/g' \> /tmp/*flow*graph\_join\_impl.h sudo cp /tmp/*flow*graph\_join\_impl.h /opt/intel/composer\_xe\_2013/tbb/include/tbb/internal/*flow*graph\_join\_impl.h

cat /opt/intel/composer\_xe\_2013.5.192/tbb/include/tbb/flow\_graph.h | perl -pe 's/(B[0-9]{1,1})/ B\$1/g' \> /tmp/flow\_graph.h sudo cp /tmp/flow\_graph.h /opt/intel/composer\_xe\_2013.5.192/tbb/include/tbb/flow\_graph.h On Mac OS X: cat /opt/intel/composer\_xe\_2013/tbb/include/tbb/internal/*flow*graph\_join\_impl.h | perl -pe 's/(B[0-9]{1,1})/ B\$1/g' \> /tmp/*flow*graph\_join\_impl.h sudo cp /tmp/*flow*graph\_join\_impl.h /opt/intel/composer\_xe\_2013/tbb/include/tbb/internal/*flow*graph\_join\_impl.h

cat /usr/include/tbb/flow\_graph.h | perl -pe 's/(B[0-9]{1,1})/ B\$1/g' \> /tmp/flow\_graph.h sudo cp /tmp/flow\_graph.h /usr/include/tbb/flow\_graph.h Test Intel TBB:

Edit /tmp/tbb.cpp: \#include <boost/asio.hpp> \#include <tbb/flow_graph.h> \#include <tbb/parallel_for_each.h> \#include <tbb/task_scheduler_init.h> \#include <iostream> \#include <vector>

struct mytask { mytask(size\_t n) : *n(n) {} void operator()() { for (int i = 0; i \< 1000000; ++i) { } // Deliberately run slow std::cerr \<\< "[" \<\< \_n \<\< "]"; } size*t \_n; };

template <typename T> struct invoker { void operator()(T& it) const { it(); } };

int main(int, char\*\*) {

tbb::task\_scheduler\_init init; // Automatic number of threads // tbb::task\_scheduler\_init init(4); // Explicit number of threads

std::vector<mytask> tasks; for (int i = 0; i \< 1000; ++i) tasks.push\_back(mytask(i));

tbb::parallel\_for\_each(tasks.begin(), tasks.end(), invoker<mytask>()); std::cerr \<\< std::endl;

return 0; } Compile and run with the Intel C++ compiler on Linux: icpc -std=c++11 -gcc-name=/usr/bin/gcc-4.7 -gxx-name=/usr/bin/g++-4.7 -I/usr/include/x86\_64-linux-gnu/c++/4.7 tbb.cpp -ltbb -lboost\_system ./a.out Compile and run with the Intel C++ compiler on Mac OS X: icpc -std=c++11 -gcc-name=/opt/local/bin/gcc-mp-4.6 -gxx-name=/opt/local/bin/g++-mp-4.6 -I /opt/local/include/gcc46/c++ tbb.cpp -ltbb -lboost\_system ./a.out Compile and run with Intel C++ compiler on Windows: icl /Qstd=c++11 tbb.cpp -Ic:-DBOOST\_ALL\_NO\_LIB c:*system-mt-s.lib -D*WIN32\_WINNT=0x0501 tbb.exe Install ISPC (Intel SPMD Program Compiler)

SPMD (single program, multiple data) is a parallelism technique wherein the same program is executed simultaneously, but on different data. Download source: sudo mkdir /ispc sudo chmod 777 /ispc git clone https://github.com/ispc/ispc.git /ispc cd /ispc Build and install: cd /ispc make

sudo ln -s /ispc/ispc /usr/bin/ispc Test Intel SPMD Program Compiler (ISPC)

cd /ispc/examples/simple

ispc -O2 --arch=x86-64 --target=sse4-x2 simple.ispc -o simple\_ispc.o -h simple\_ispc.h icpc -O3 -Wall simple.cpp simple\_ispc.o -o simple

./simple Install SDL (Simple DirectMedia Layer)

Install SDL on Linux or Mac OS X

Simple DirectMedia Layer is a cross-platform development library designed to provide low level access to audio, keyboard, mouse, joystick, and graphics hardware via OpenGL and Direct3D. Install prerequisites (for Linux): sudo apt-get install libxext-dev libgles2-mesa-dev libgl1-mesa-dev Check OpenGL support (for Linux): glxinfo | grep "OpenGL version" Download source, build, and install: sudo mkdir /libsdl sudo chmod 777 /libsdl cd /libsdl wget 'http://www.libsdl.org/release/SDL2-2.0.0.tar.gz' tar -xzvf SDL2-2.0.0.tar.gz Build and install (on Linux): cd /libsdl/SDL2-2.0.0 ./configure make -j8 sudo make install Build and install (on OSX): cd /libsdl/SDL2-2.0.0 ./configure make -j8 sudo make install

sudo cp -Ra /usr/local/include/SDL2 /usr/include/ Install SDL On Windows

NOTE: This assumes that you have Microsoft Visual Studio Express 2012 for Desktop installed Install the Microsoft DirectX Software Development Kit: http://www.microsoft.com/en-us/download/search.aspx?q=directx From cygwin: mkdir /cygdrive/c/libsdl chmod 777 /cygdrive/c/libsdl cd /cygdrive/c/libsdl

wget 'http://www.libsdl.org/release/SDL2-2.0.0.tar.gz' tar -xzvf SDL2-2.0.0.tar.gz

mkdir /cygdrive/c/libsdl/SDL2 cp -Ra /cygdrive/c/libsdl/SDL2-2.0.0/include/\* /cygdrive/c/libsdl/SDL2 Open c:2-2.0.0\_VS2012EE.sln Build the .dll and .lib files in Release and Win64 mode Test SDL:

Edit /tmp/sdl-test.cpp: \#include <stdio.h> \#include <stdlib.h>

/\* If using gl3.h */ /* Ensure we are using opengl's core profile only \*/ \#ifndef **APPLE** \#define GL3\_PROTOTYPES 1 \#endif

ifdef **linux \#include <GLES3/gl3.h> \#elif **APPLE\_* \#include "gl3.h" \#elif *WIN32
=======================================================================================

//\#include <gl3.h> \#include <SDL2/SDL_opengl.h> \#endif

include <SDL2/SDL.h>
====================

define PROGRAM\_NAME "Tutorial1"
================================

ifdef \_WIN32 \#undef main \#endif
==================================

/\* A simple function that prints a message, the error code returned by SDL, \* and quits the application */ void sdldie(const char *msg) { printf("%s: %s", msg, SDL\_GetError()); SDL\_Quit(); exit(1); }

void checkSDLError(int line = -1) { \#ifndef NDEBUG const char *error = SDL\_GetError(); if (*error != '') { printf("SDL Error: %s", error); if (line != -1) printf(" + line: %i", line); SDL\_ClearError(); } \#endif }

/\* Our program's entry point */ int main(int argc, char *argv[]) { SDL\_Window *mainwindow; /* Our window handle */ SDL\_GLContext maincontext; /* Our opengl context handle \*/

if (SDL\_Init(SDL\_INIT\_VIDEO) \< 0) /\* Initialize SDL's Video subsystem */ sdldie("Unable to initialize SDL"); /* Or die on error \*/

/\* Request opengl 3.2 context. \* SDL doesn't have the ability to choose which profile at this time of \* writing, \* but it should default to the core profile \*/ SDL\_GL\_SetAttribute(SDL\_GL\_CONTEXT\_MAJOR\_VERSION, 3); SDL\_GL\_SetAttribute(SDL\_GL\_CONTEXT\_MINOR\_VERSION, 2);

/\* Turn on double buffering with a 24bit Z buffer. \* You may need to change this to 16 or 32 for your system \*/ SDL\_GL\_SetAttribute(SDL\_GL\_DOUBLEBUFFER, 1); SDL\_GL\_SetAttribute(SDL\_GL\_DEPTH\_SIZE, 24);

/\* Create our window centered at 512x512 resolution */ mainwindow = SDL\_CreateWindow(PROGRAM\_NAME, SDL\_WINDOWPOS\_CENTERED, SDL\_WINDOWPOS\_CENTERED, 512, 512, SDL\_WINDOW\_OPENGL | SDL\_WINDOW\_SHOWN); if (!mainwindow) /* Die if creation failed \*/ sdldie("Unable to create window");

checkSDLError(**LINE**);

/\* Create our opengl context and attach it to our window \*/ maincontext = SDL\_GL\_CreateContext(mainwindow); checkSDLError(**LINE**);

/\* This makes our buffer swap syncronized with the monitor's vertical refresh \*/ SDL\_GL\_SetSwapInterval(1);

/\* Clear our buffer with a red background */ glClearColor(1.0, 0.0, 0.0, 1.0); glClear(GL\_COLOR\_BUFFER\_BIT); /* Swap our back buffer to the front */ SDL\_GL\_SwapWindow(mainwindow); /* Wait 2 seconds \*/ SDL\_Delay(2000);

/\* Same as above, but green \*/ glClearColor(0.0, 1.0, 0.0, 1.0); glClear(GL\_COLOR\_BUFFER\_BIT); SDL\_GL\_SwapWindow(mainwindow); SDL\_Delay(2000);

/\* Same as above, but blue \*/ glClearColor(0.0, 0.0, 1.0, 1.0); glClear(GL\_COLOR\_BUFFER\_BIT); SDL\_GL\_SwapWindow(mainwindow); SDL\_Delay(2000);

/\* Delete our opengl context, destroy our window, and shutdown SDL \*/ SDL\_GL\_DeleteContext(maincontext); SDL\_DestroyWindow(mainwindow); SDL\_Quit();

return 0; } Build and run test SDL program:

Build and run with gcc on Linux: cd /tmp g++ sdl-test.cpp -o sdl-test -lGL -lSDL2 ./sdl-test Build and run with Intel C++ compiler on Linux: cd /tmp icpc -std=c++11 -gcc-name=/usr/bin/gcc-4.7 -gxx-name=/usr/bin/g++-4.7 -I/usr/include/x86\_64-linux-gnu/c++/4.7 sdl-test.cpp -lGL -lSDL2 -o sdl-test ./sdl-test Build and run with clang on Linux: cd /tmp clang++ sdl-test.cpp -o sdl-test -lGL -lSDL2 ./sdl-test Build and run with gcc on OS X: cd /tmp g++ -std=c++1y -lSDL2 -framework OpenGL -framework Cocoa sdl-test.cpp -I/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.8.sdk/System/Library/Frameworks/OpenGL.framework/Versions/A/Headers/ -o sdl-test ./sdl-test Build and run with Intel C++ compiler on OS X: cd /tmp icpc -std=c++11 -lSDL2 -framework OpenGL -framework Cocoa sdl-test.cpp -I/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.8.sdk/System/Library/Frameworks/OpenGL.framework/Versions/A/Headers/ -o sdl-test ./sdl-test Build and run with clang on OS X: cd /tmp clang++ -std=c++1y -lSDL2 -framework OpenGL -framework Cocoa sdl-test.cpp -I/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.8.sdk/System/Library/Frameworks/OpenGL.framework/Versions/A/Headers/ -o sdl-test ./sdl-test Build and run with the Intel C++ Compiler on Windows: icl /Qstd=c++11 -Ic:sdl.cpp c:2-2.0.0642.lib c:2-2.0.0642main.lib opengl32.lib glu32.lib copy c:2-2.0.0642.dll . sdl.exe Install gcutil for Google Compute Engine

download gcutil https://code.google.com/p/google-compute-engine-tools/downloads/list

cd /tmp wget https://google-compute-engine-tools.googlecode.com/files/gcutil-1.8.3.tar.gz tar xzvf gcutil-1.8.3.tar.gz sudo mv gcutil-1.8.3 /gcutil create a symbolic link to the gcutil binary

sudo rm -rf /usr/local/bin/gcutil sudo ln -s /gcutil/gcutil /usr/bin/gcutil Authenticate to Google Compute Engine

gcutil auth --project=<project ID> specify a default project id:

gcutil getproject --project=<project-id> --cache\_flag\_values Install gsutil for Google Cloud Storage

download gsutil

sudo rm -rf /usr/local/bin/gsutil

cd /tmp wget 'http://storage.googleapis.com/pub/gsutil.tar.gz' tar -xzvf gsutil.tar.gz sudo mv /tmp/gsutil /gsutil create a symbolic link to the gsutil binary

sudo ln -s /gsutil/gsutil /usr/bin/gsutil authenticate

gsutil config copy objects to your bucket in parallel

gsutil -m cp index.html file2.jpg file3.txt gs://mybucket/ Automatically chdir into your development directory upon login (optional):

Type this at your bash prompt: echo "cd /INSERT\_YOUR\_PROJECT\_DIRECTORY\_HERE" \>\> \~/.bashrc Increase the maximum number of open file descriptors (optional):

sudo su chmod +w /etc/sysctl.conf echo "fs.file-max = 100000000" \>\> /etc/sysctl.conf chmod -w /etc/sysctl.conf sysctl -p exit

sudo su chmod +w /etc/pam.d/su echo "session required pam\_limits.so" \>\> /etc/pam.d/su echo "\* - nofile 100000" \>\> /etc/security/limits.conf chmod -w /etc/pam.d/su exit Now, logout and login. Generate new host keys

sudo rm -rf /etc/ssh/ssh\_host\_\* sudo ssh-keygen -A sudo service ssh restart Install cdecl for explaining C and C++ type declarations

sudo apt-get install cdecl Test cdecl: c++decl explain "char \* const (*(* const bar)[5])(int )" Install libevent

Download source in Linux or Mac OS X: cd /tmp wget 'http://sourceforge.net/projects/levent/files/libevent/libevent-2.1/libevent-2.1.3-alpha.tar.gz/download' tar -xzvf libevent*.gz cd libevent* Download source in Windows from Cygwin: cd /tmp wget 'http://sourceforge.net/projects/levent/files/libevent/libevent-2.1/libevent-2.1.3-alpha.tar.gz/download' tar -xzvf libevent*.gz cd libevent* mkdir /cygdrive/c/libevent mv ./\* /cygdrive/c/libevent Install libevent on Linux: ./configure --prefix=/usr --enable-static --disable-shared --enable-gcc-hardening "CXX=/usr/bin/g++-4.9 \({BUILD64}" CC="/usr/bin/gcc-4.9 \){BUILD64}"

make -j8 sudo make install Install libevent on Mac OS X: ./configure --prefix=/usr --enable-static --disable-shared --enable-gcc-hardening "CXX=/opt/local/bin/g++ \({BUILD64}" CC="/opt/local/bin/gcc \){BUILD64}"

make -j8 sudo make install Install libevent on Windows from cmd.exe:

Edit c:.nmake to look like this: \# WATCH OUT! This makefile is a work in progress. -*- makefile -*- \# \# I'm not very knowledgeable about MSVC and nmake beyond their most basic \# aspects. If anything here looks wrong to you, please let me know.

If OPENSSL\_DIR is not set, builds without OpenSSL support. If you want
=======================================================================

OpenSSL support, you can set the OPENSSL\_DIR variable to where you
===================================================================

installed OpenSSL. This can be done in the environment:
=======================================================

set OPENSSL\_DIR=c:\# Or on the nmake command line:
===================================================

nmake OPENSSL\_DIR=C:-f Makefile.nmake
======================================

Or by uncommenting the following line here in the makefile...
=============================================================

OPENSSL\_DIR=c:
===============

!IFDEF OPENSSL\_DIR SSL\_CFLAGS=/I\$(OPENSSL\_DIR)/DEVENT\_*HAVE*OPENSSL /D\_WIN64=1 /DWIN64=1 /MT /Ox /DNDEBUG !ELSE SSL\_CFLAGS=/D\_WIN64=1 /DWIN64=1 /MT /Ox /DNDEBUG !ENDIF

Needed for correctness
======================

CFLAGS=/IWIN32-Code /Iinclude /Icompat /DHAVE\_CONFIG\_H /D\_WIN64=1 /DWIN64=1 /MT /Ox /DNDEBUG /I. \$(SSL\_CFLAGS)

For optimization and warnings
=============================

CFLAGS=\$(CFLAGS) /Ox /W3 /wd4996 /nologo

XXXX have a debug mode
======================

LIBFLAGS=/nologo /MACHINE:X64

CORE\_OBJS=event.obj buffer.obj bufferevent.obj bufferevent\_sock.obj
 bufferevent\_pair.obj listener.obj evmap.obj log.obj evutil.obj
 strlcpy.obj signal.obj bufferevent\_filter.obj evthread.obj
 bufferevent\_ratelim.obj evutil\_rand.obj evutil\_time.obj WIN\_OBJS=win32select.obj evthread\_win32.obj buffer\_iocp.obj
 event\_iocp.obj bufferevent\_async.obj EXTRA\_OBJS=event\_tagging.obj http.obj evdns.obj evrpc.obj

!IFDEF OPENSSL\_DIR SSL\_OBJS=bufferevent\_openssl.obj SSL\_LIBS="c:Files (x86)SDKs.1A6432.Lib" "c:Files (x86)SDKs.1A6432.lib" "c:Files (x86)SDKs.1A6432.lib" "c:Files (x86)
soft SDKs.1A6432.lib" "c:Files (x86)SDKs.1A6432.lib" "c:Files (x86)SDKs.1A6432.lib" libevent\_openssl.lib \((OPENSSL_DIR)\lib\libeay32.lib \)(OPENSSL\_DI
R)32.lib !ELSE SSL\_OBJS= SSL\_LIBS= !ENDIF

ALL\_OBJS=\((CORE_OBJS) \)(WIN\_OBJS) \((EXTRA_OBJS) \)(SSL\_OBJS) STATIC\_LIBS=libevent\_core.lib libevent\_extras.lib libevent.lib \$(SSL\_LIBS)

all: static\_libs

static\_libs: \$(STATIC\_LIBS)

libevent\_core.lib: \((CORE_OBJS) \)(WIN\_OBJS) lib \((LIBFLAGS) \)(CORE\_OBJS) \$(WIN\_OBJS) /out:libevent\_core.lib

libevent\_extras.lib: \((EXTRA_OBJS)         lib \)(LIBFLAGS) \$(EXTRA\_OBJS) /out:libevent\_extras.lib

libevent.lib: \((CORE_OBJS) \)(WIN\_OBJS) \((EXTRA_OBJS)         lib \)(LIBFLAGS) \((CORE_OBJS) \)(EXTRA\_OBJS) \$(WIN\_OBJS) /out:libevent.lib

libevent\_openssl.lib: \((SSL_OBJS)         lib \)(LIBFLAGS) \$(SSL\_OBJS) /out:libevent\_openssl.lib

clean: del \((ALL_OBJS)         del \)(STATIC\_LIBS) cd test \$(MAKE) /F Makefile.nmake clean cd ..

tests: cd test !IFDEF OPENSSL\_DIR \((MAKE) OPENSSL_DIR=\)(OPENSSL\_DIR) /F Makefile.nmake !ELSE \$(MAKE) /F Makefile.nmake !ENDIF cd .. Build as follows: cd c:nmake OPENSSL\_DIR=C:-f Makefile.nmake Test libevent:

Edit /tmp/libevent.c as follows: \#ifdef *WIN32 \#include <winsock2.h> \#else /\* For sockaddr*in */ \#include <netinet/in.h> /* For socket functions \*/ \#include <sys/socket.h> \#include <errno.h> \#include <unistd.h> \#endif

/\* For fcntl \*/ \#include <fcntl.h>

include <event2/event.h>
========================

include <event2/buffer.h>
=========================

include <event2/bufferevent.h>
==============================

include <assert.h>
==================

include <string.h>
==================

include <stdlib.h>
==================

include <stdio.h>
=================

define MAX\_LINE 16384
======================

void do\_read(evutil\_socket\_t fd, short events, void *arg); void do\_write(evutil\_socket\_t fd, short events, void *arg);

char rot13\_char(char c) { /\* We don't want to use isalpha here; setting the locale would change \* which characters are considered alphabetical. \*/ if ((c \>= 'a' && c \<= 'm') || (c \>= 'A' && c \<= 'M')) return c + 13; else if ((c \>= 'n' && c \<= 'z') || (c \>= 'N' && c \<= 'Z')) return c - 13; else return c; }

void readcb(struct bufferevent *bev, void *ctx) { struct evbuffer *input, *output; char \*line; size\_t n; int i; input = bufferevent\_get\_input(bev); output = bufferevent\_get\_output(bev);

printf("in readcb");

while ((line = evbuffer\_readln(input, &n, EVBUFFER\_EOL\_LF))) { for (i = 0; i \< n; ++i) line[i] = rot13\_char(line[i]); evbuffer\_add(output, line, n); evbuffer\_add(output, "", 1); free(line); }

if (evbuffer\_get\_length(input) \>= MAX\_LINE) { /\* Too long; just process what there is and go on so that the buffer \* doesn't grow infinitely long. \*/ char buf[1024]; while (evbuffer\_get\_length(input)) { int n = evbuffer\_remove(input, buf, sizeof(buf)); for (i = 0; i \< n; ++i) buf[i] = rot13\_char(buf[i]); evbuffer\_add(output, buf, n); } evbuffer\_add(output, "", 1); }

printf("finishing readcb"); }

void errorcb(struct bufferevent *bev, short error, void *ctx) { if (error & BEV\_EVENT\_EOF) { /\* connection has been closed, do any clean up here */ /* ... */ } else if (error & BEV\_EVENT\_ERROR) { /* check errno to see what error occurred */ /* ... */ } else if (error & BEV\_EVENT\_TIMEOUT) { /* must be a timeout event handle, handle it */ /* ... \*/ } bufferevent\_free(bev); }

void do\_accept(evutil\_socket\_t listener, short event, void *arg) { struct event\_base *base = arg; struct sockaddr\_storage ss; socklen\_t slen = sizeof(ss); int fd = accept(listener, (struct sockaddr *)&ss, &slen); if (fd \< 0) { perror("accept"); } else if (fd \> FD\_SETSIZE) { close(fd); } else { printf("Got new connection"); struct bufferevent *bev; evutil\_make\_socket\_nonblocking(fd); bev = bufferevent\_socket\_new(base, fd, BEV\_OPT\_CLOSE\_ON\_FREE); bufferevent\_setcb(bev, readcb, NULL, errorcb, NULL); bufferevent\_setwatermark(bev, EV\_READ, 0, MAX\_LINE); bufferevent\_enable(bev, EV\_READ | EV\_WRITE); } }

void run(void) { evutil\_socket\_t listener; struct sockaddr\_in sin; struct event\_base *base; struct event *listener\_event;

ifdef *WIN32 WSADATA wsa*data;
==============================

WSAStartup(0x0201, &wsa\_data); \#endif

base = event\_base\_new(); if (!base) return; /*XXXerr*/

sin.sin\_family = AF\_INET; sin.sin\_addr.s\_addr = 0; sin.sin\_port = htons(40713);

listener = socket(AF\_INET, SOCK\_STREAM, 0); evutil\_make\_socket\_nonblocking(listener);

ifndef WIN32
============

{ int one = 1; setsockopt(listener, SOL\_SOCKET, SO\_REUSEADDR, &one, sizeof(one)); } \#endif

if (bind(listener, (struct sockaddr \*)&sin, sizeof(sin)) \< 0) { perror("bind"); return; }

if (listen(listener, 16) \< 0) { perror("listen"); return; }

listener\_event = event\_new(base, listener, EV\_READ | EV\_PERSIST, do\_accept, (void *)base); /*XXX check it \*/ event\_add(listener\_event, NULL);

event\_base\_dispatch(base);

printf("Finished setting up"); }

int main(int c, char \*\*v) { printf("Running"); setvbuf(stdout, NULL, \_IONBF, 0);

run(); return 0; } Build and run on Linux with gcc: cd /tmp gcc -std=c11 test.c -levent -o libevent-test ./libevent-test & netcat localhost 40713 \# type something in to test out the ROT-13 server Build and run on Linux with Intel C Compiler: cd /tmp icc -std=c99 test.c -levent -o libevent-test ./libevent-test & netcat localhost 40713 \# type something in to test out the ROT-13 server Build and run on OS X with Intel C Compiler: sudo port install gnetcat

cd /tmp icc -std=c99 test.c -levent -o libevent-test ./libevent-test & gnetcat localhost 40713 \# type something in to test out the ROT-13 server Build and run on Windows with Intel C Compiler from cmd.exe: icl /Qstd=c99 libevent.c /Ic:/Ic:32-Code c:.lib ws2\_32.lib Advapi32.lib libevent.exe

from cygwin:
============

nc localhost 40713 \# type something in to test out the ROT-13 server Install Boehm-Demers-Weiser conservative garbage collector

Satisfy prerequisites: sudo apt-get install libtool Download and build: sudo mkdir /boehmgc sudo chmod 777 /boehmgc

cd /boehmgc git clone git://github.com/ivmai/libatomic\_ops.git git clone git://github.com/ivmai/bdwgc.git ln -s /boehmgc/libatomic\_ops /boehmgc/bdwgc/libatomic\_ops cd bdwgc/ autoreconf -vif sudo apt-cache search libtool sudo apt-get install libtool sudo apt-cache search libtool autoreconf -vif automake --add-missing ./configure make -j8 sudo make install Test boehmgc

Edit /tmp/boehmgc.c: \#include <stdio.h> \#include <assert.h>

include <gc/leak_detector.h>
============================

int main() { GC\_find\_leak = 1; int \*p[10]; int i; for (i = 0; i \< 10; ++i) { p[i] = malloc(sizeof(int) + i); } for (i = 1; i \< 10; ++i) { free(p[i]); } for (i = 0; i \< 9; ++i) { p[i] = malloc(sizeof(int) + i); } CHECK\_LEAKS(); } Build and run: gcc -O0 -g -Wall -std=c99 boehmgc.c -DSAVE\_CALL\_CHAIN -lgc ./a.out Edit /tmp/boehmgc2.c: \#include <gc.h> \#include <assert.h> \#include <stdio.h>

int main() { int i;

GC\_INIT(); for (i = 0; i \< 10000000; ++i) { int **p = (int **)GC\_MALLOC(sizeof(int *)); int *q = (int *)GC\_MALLOC\_ATOMIC(sizeof(int)); assert(*p == 0); *p = (int *)GC\_REALLOC(q, 2 \* sizeof(int)); if (i % 100000 == 0) printf("Heap size = %d", GC\_get\_heap\_size()); } return 0; } Build and run: cd /tmp gcc -O0 -g -Wall -std=c99 boehmgc2.c -lgc valgrind --leak-check=yes ./a.out Configure Emacs

enable frame-fns

cd \~/.emacs.d wget 'http://www.emacswiki.org/emacs-en/download/frame-fns.el' wget 'http://www.emacswiki.org/emacs-en/download/frame-cmds.el' Install Yasnippet For Emacs

cd \~/.emacs.d git clone https://github.com/capitaomorte/yasnippet

sudo mkdir /snippets sudo chmod 777 /snippets cp -Ra \~/.emacs.d/yasnippet/snippets/\* /snippets/ Install Emacs Autocomplete Mode

NOTE: There is an incompatibility between older versions of autocomplete and yasnippet. Therefore, we are pulling directly from trunk: cd /tmp git clone https://github.com/auto-complete/auto-complete.git git clone https://github.com/auto-complete/popup-el.git cp popup-el/popup.el auto-complete/ cp popup-el/popup.el auto-complete/lib/popup/ cd auto-complete/ make make install When prompted, tell autocomplete to install into: \~/.emacs.d Download clang autocomplete aync: cd /tmp git clone https://github.com/Golevka/emacs-clang-complete-async.git cd /tmp/emacs-clang-complete-async/ make cp auto-complete-clang-async.el \~/.emacs.d/ cp clang-complete \~/.emacs.d/ Install xcscope

cd /tmp git clone https://github.com/To1ne/xcscope.git cp xcscope/xcscope.el \~/.emacs.d/ sudo cp /tmp/xcscope/cscope-indexer /usr/bin sudo chmod +x /usr/bin/cscope-indexer Also see: How to use cscope to jump to OpenGL library function definitions from inside of emacs Use Google's C++ Style

download: cd \~/.emacs.d wget 'http://google-styleguide.googlecode.com/svn/trunk/google-c-style.el' Enable Emacs Autopair Mode:

download: cd \~/.emacs.d wget --no-check-certificate 'https://raw.github.com/capitaomorte/autopair/master/autopair.el' Enable "google this" functionality for emacs

cd /tmp git clone https://github.com/Bruce-Connor/emacs-google-this cp emacs-google-this/google-this.el \~/.emacs.d/ Enable flymake mode with syntax error message display for C and C++

sudo apt-get install cmake

cd \~/.emacs.d wget 'http://www.emacswiki.org/emacs/download/flymake-cursor.el'

cd /tmp git clone https://github.com/alamaison/emacs-cmake-project.git cp /tmp/emacs-cmake-project/cmake-project.el \~/.emacs.d/ Setup clang-format (automatically format C/C++) for use with emacs

Select the Google C/C++ formatting style: sed -i 's/LLVM/Google/g' /llvm/llvm/tools/clang/tools/clang-format/clang-format.el Edit \~/.emacs to look this like:

;; show column number (column-number-mode t)

(add-to-list 'load-path "\~/.emacs.d") (if (functionp 'tool-bar-mode) (tool-bar-mode -1)) (if (functionp 'scroll-bar-mode) (scroll-bar-mode -1))

(if (functionp 'load-theme) (load-theme 'manoj-dark t))

(when window-system (require 'frame-fns)) (when window-system (require 'frame-cmds))

;; switch to fullscreen mode: ;; also make new frames spawned by 'emacsclient -c -n' fullscreen, too (defun my-frame-config (frame) "Custom behaviours for new frames." (with-selected-frame frame (set-frame-parameter nil 'fullscreen 'fullboth) (if (functionp 'maximize-frame)(maximize-frame)) (if (functionp 'maximize-frame-horizontally)(maximize-frame-horizontally)) (if (functionp 'maximize-frame-vertically)(maximize-frame-vertically)) (set-fringe-mode 0) )) ;; run now (when window-system (my-frame-config (selected-frame))) ;; and later (add-hook 'after-make-frame-functions 'my-frame-config)

(defun toggle-fullscreen (&optional f) (interactive) (let ((current-value (frame-parameter nil 'fullscreen))) (set-frame-parameter nil 'fullscreen (if (equal 'fullboth current-value) (if (boundp 'old-fullscreen) old-fullscreen nil) (progn (setq old-fullscreen current-value) 'fullboth))))) ; Make new frames fullscreen by default. Note: this hook doesn't do ; anything to the initial frame if it's in your .emacs, since that file is ; read *after* the initial frame is created. ;;(add-hook 'after-make-frame-functions 'toggle-fullscreen) ;;(run-with-idle-timer 0.1 nil 'toggle-fullscreen)

;; flash instead of that annoying bell (setq visible-bell t)

;; Format the title-bar to always include the buffer name (setq frame-title-format "%b")

;; Scroll line by line (setq scroll-step 1)

(menu-bar-mode 0)

(custom-set-variables ;; custom-set-variables was added by Custom. ;; If you edit it by hand, you could mess it up, so be careful. ;; Your init file should contain only one such instance. ;; If there is more than one, they won't work right. '(custom-safe-themes (quote ("88d556f828e4ec17ac074077ef9dcaa36a59dccbaa6f2de553d6528b4df79cbd" "e16a771a13a202ee6e276d06098bc77f008b73bbac4d526f160faa2d76c1dd0e" "8aebf25556399b58091e533e455dd50a6a9cba958cc4ebb0aab175863c25b9a4" default))) '(inhibit-startup-screen t))

(setq-default inhibit-startup-message 't initial-scratch-message 'nil save-place t scroll-preserve-screen-position 1 cursor-in-non-selected-windows nil scroll-margin 1 )

(custom-set-faces ;; custom-set-faces was added by Custom. ;; If you edit it by hand, you could mess it up, so be careful. ;; Your init file should contain only one such instance. ;; If there is more than one, they won't work right. )

;;; Ctrl-h = Backspace (global-set-key [8] 'delete-backward-char)

(global-unset-key [(control shift v)]) ;;use page-up (global-set-key [(control shift v)] 'clipboard-yank) (global-unset-key [(control shift c)]) (global-set-key [(control shift c)] 'clipboard-kill-ring-save)

;; in every buffer, the line which contains the cursor will be fully highlighted (global-hl-line-mode 1)

;; make buffer names unique (require 'uniquify) (setq uniquify-buffer-name-style 'post-forward-angle-brackets)

;; enable inline images: (iimage-mode)

;; treat .h files as c files (add-to-list 'auto-mode-alist '("\\.h\\'" . c-mode))

;; show matching parens: (show-paren-mode 1) (setq show-paren-delay 0)

(require 'cedet) (require 'cedet-files) (setq semantic-load-turn-useful-things-on t) (global-ede-mode 1) (require 'semantic) ;; Activate semantic (semantic-mode 1)

(require 'semantic/sb) (require 'srecode) (global-semanticdb-minor-mode 1) (global-semantic-decoration-mode 1) (global-semantic-highlight-func-mode 1) (global-semantic-stickyfunc-mode -1) (global-semantic-mru-bookmark-mode 1)

;; Try to make completions when not typing '(semantic-complete-inline-analyzer-displayor-class (quote semantic-displayor-tooltip)) '(semantic-complete-inline-analyzer-idle-displayor-class (quote semantic-displayor-tooltip)) (global-semantic-idle-completions-mode 1) (global-semantic-idle-scheduler-mode 1) ;; disable global-semantic-idle-summary-mode because it can interfere with flymake error messages: ;;(global-semantic-idle-summary-mode 1)

(add-to-list 'semantic-default-submodes 'global-semanticdb-minor-mode) (add-to-list 'semantic-default-submodes 'global-semantic-mru-bookmark-mode) (add-to-list 'semantic-default-submodes 'global-semantic-idle-local-symbol-highlight-mode) (add-to-list 'semantic-default-submodes 'global-semantic-idle-scheduler-mode) (add-to-list 'semantic-default-submodes 'global-semantic-idle-completions-mode) (add-to-list 'semantic-default-submodes 'global-semantic-idle-summary-mode) (add-to-list 'semantic-default-submodes 'global-semantic-decoration-mode)

(semantic-add-system-include "/usr/include/GL" 'c++-mode) (semantic-add-system-include "/usr/include/GL" 'c-mode) (semantic-add-system-include "/usr/include" 'c++-mode) (semantic-add-system-include "/usr/include" 'c-mode) (semantic-add-system-include "/usr/include/google" 'c++-mode) (semantic-add-system-include "/usr/include/google" 'c-mode)

;; Enable yasnippet (add-to-list 'load-path "\~/.emacs.d/yasnippet") (require 'yasnippet) ;; Develop and keep personal snippets under \~/emacs.d/mysnippets (setq yas/root-directory '("/earthserver.com/snippets")) ;; Load the snippets ;; Map \`yas/load-directory' to every element (mapc 'yas/load-directory yas/root-directory) (yas-global-mode 1)

;;--------------------------------------------------------------- ;; START enable C/C++ autocomplete for emacs (add-to-list 'load-path "\~/.emacs.d") (require 'cl) (require 'auto-complete-config) (add-to-list 'ac-dictionary-directories "\~/.emacs.d/ac-dict") (ac-config-default) (require 'auto-complete-clang-async)

;; Select candidates with C-n/C-p only when completion menu is displayed: (setq ac-use-menu-map t) (define-key ac-menu-map "C-n" 'ac-next) (define-key ac-menu-map "C-p" 'ac-previous)

(require 'xcscope) (setq cscope-index-recursively t)

(setq-default ac-sources '(ac-source-abbrev ac-source-dictionary ac-source-words-in-same-mode-buffers ac-source-filename ac-source-yasnippet)) (setq ac-candidate-limit 200) ;; do not stall with too many results (setq ac-auto-start 0) (setq ac-auto-show-menu t) (setq ac-quick-help-delay 0) (setq ac-use-fuzzy 1.5) (setq ac-show-menu-immediately-on-auto-complete t) (setq ac-expand-on-auto-complete nil) (setq ac-quick-help-height 20) (setq ac-menu-height 20) (ac-set-trigger-key "TAB") (define-key ac-mode-map [(control tab)] 'auto-complete)

(defun ac-cc-mode-setup () (setq ac-clang-complete-executable "\~/.emacs.d/clang-complete")

(setq clang-completion-suppress-error 't)

(defvar clangcomplete-flags-global (append ;; for c++ use this: (list "-std=c++1y") ;; for c use this: ;;(list "-std=c11") (mapcar '(lambda (inc) (concat "-I" inc)) (split-string (let\* ;; for c++ use this: ((out (shell-command-to-string "gcc -xc++ -E -v /dev/null 2\>&1 | sed -e 's/\\/.\(/ /g'"))                   ;; for c use this:                   ;;((out (shell-command-to-string "gcc -xc -E -v /dev/null 2>&1 | sed -e 's/\\\/\.\)/ /g'")) (st (string-match "\> search starts here" out)) (se (match-end 0)) (eb (string-match "End of" out))) (with-temp-buffer (insert out) (goto-char se) (end-of-line) (forward-char 1) (let ((buf (buffer-substring-no-properties (point) eb))) buf)))))))

(setq ac-clang-cflags clangcomplete-flags-global)

;; Autocomplete code for Google Chrome native client (NaCl), if it is installed: (if (file-exists-p "/nacl\_sdk/pepper\_canary/include") (setq ac-clang-cflags (append ac-clang-cflags (list "-I/nacl\_sdk/pepper\_canary/include"))))

;; Autocomplete code for Intel C/C++ compiler headers, if it is installed: (if (file-exists-p "/opt/intel/include") (setq ac-clang-cflags (append ac-clang-cflags (list "-I/opt/intel/include"))))

(setq ac-sources '(ac-source-clang-async))

;; to debug, run "ps -ef | grep clang" while you are editing a .cpp document in emacs. You should see something that looks like this: ;; \~/.emacs.d/clang-complete -cc1 -fsyntax-only -x c++ -I/opt/intel/composer\_xe\_2013.5.192/mkl/include -I/opt/intel/composer\_xe\_2013.5.192/tbb/include -I/usr/lib/gcc/x86\_64-linux-gnu/4.9.0/../../../../include/c++/4.9.0 -I/usr/lib/gcc/x86\_64-linux-gnu/4.9.0/../../../../include/c++/4.9.0/x86\_64-linux-gnu -I/usr/lib/gcc/x86\_64-linux-gnu/4.9.0/../../../../include/c++/4.9.0/backward -I/usr/lib/gcc/x86\_64-linux-gnu/4.9.0/include -I/usr/local/include -I/usr/lib/gcc/x86\_64-linux-gnu/4.9.0/include-fixed -I/usr/include/x86\_64-linux-gnu -I/usr/include -I/opt/intel/include -fcxx-exceptions -fexceptions -fno-caret-diagnostics -std=c++1y myprogram.cpp

(ac-clang-launch-completion-process) (ac-clang-update-cmdlineargs) )

(defun my-ac-config () (add-hook 'c-mode-common-hook 'ac-cc-mode-setup) (add-hook 'auto-complete-mode-hook 'ac-common-setup) (global-auto-complete-mode t))

(my-ac-config) ;; END enable C/C++ autocomplete for emacs ;;---------------------------------------------------------------

;; Use Google's C Style: (require 'google-c-style) (add-hook 'c-mode-common-hook 'google-set-c-style) (add-hook 'c-mode-common-hook 'google-make-newline-indent)

(require 'autopair) (autopair-global-mode) ;; enable autopair in all buffers '(autopair-blink t) '(autopair-autowrap t) ;; prevent the { (opening brace) character from being autopaired in C++ comments: (add-hook 'c++-mode-hook \#'(lambda () (push ?{ (getf autopair-dont-pair :comment)))) ;; disable pair creation when there already is a non-whitespace character after the cursor (defun autopair-dont-if-point-non-whitespace (action pair pos-before) (if (or (eq 'opening action) (eq 'insert-quote action)) (let ((delete? (save-excursion ;;move forward past the paired element (goto-char (+ (point) 1)) (let\* ((eol? (eq (point) (line-end-position))) (next-whitespace (save-excursion (search-forward " " (point-max) t) (point))) (next-char-is-whitespace? (eq next-whitespace (+ (point) 1))) (delete? (not (or eol? next-char-is-whitespace?)))) delete?)))) (if delete? (delete-char 1) 't)) 't)) (add-hook 'c++-mode-hook \#'(lambda () (setq autopair-handle-action-fns (list \#'autopair-default-handle-action \#'autopair-dont-if-point-non-whitespace)))) (add-hook 'c-mode-hook \#'(lambda () (setq autopair-handle-action-fns (list \#'autopair-default-handle-action \#'autopair-dont-if-point-non-whitespace))))

;; automatically reload snippets after saving: (defun reload-snippets () (interactive) (yas-reload-all) (yas-recompile-all) (yas-reload-all) (yas-recompile-all) ) (defun snippet-mode-before-save () (interactive) (when (eq major-mode 'snippet-mode) (reload-snippets))) (add-hook 'after-save-hook 'snippet-mode-before-save)

;; map specific directory to snippet-mode: (add-to-list 'auto-mode-alist '("\^/earthserver.com/snippets/" . snippet-mode))

;; enable hippie-expand (global-set-key (kbd "M-/") 'hippie-expand) (setq hippie-expand-try-functions-list '(yas/hippie-try-expand try-expand-dabbrev try-expand-dabbrev-all-buffers try-expand-dabbrev-from-kill try-complete-file-name-partially try-complete-file-name try-expand-all-abbrevs try-expand-list try-expand-line try-complete-lisp-symbol-partially try-complete-lisp-symbol))

(require 'google-this) (google-this-mode 1)

;;--------------------------------------------------------------- ;; START enable flymake (require 'flymake) (require 'cmake-project) (require 'flymake-cursor)

(setq flymake-gui-warnings-enabled nil) (set-variable 'flymake-start-syntax-check-on-newline nil)

(defun maybe-cmake-project-hook () (if (file-exists-p "CMakeLists.txt") (cmake-project-mode))) (add-hook 'c-mode-hook 'maybe-cmake-project-hook) (add-hook 'c++-mode-hook 'maybe-cmake-project-hook)

(defun turn-on-flymake-mode() (if (and (boundp 'flymake-mode) flymake-mode) () (flymake-mode t)))

(add-hook 'c-mode-common-hook (lambda () (turn-on-flymake-mode))) (add-hook 'c++-mode-hook (lambda () (turn-on-flymake-mode)))

(defun cmake-project-current-build-command () "Command line to compile current project as configured in the build directory." (concat "cmake --build " (shell-quote-argument (expand-file-name cmake-project-build-directory)) " -- -j 1" ))

(defun cmake-project-flymake-init () (list (executable-find "cmake") (list "--build" (expand-file-name cmake-project-build-directory) "--" "-j" "1" ))) ;; END enable flymake ;;---------------------------------------------------------------

(setq make-backup-files nil)

(load "/llvm/llvm/tools/clang/tools/clang-format/clang-format.el") (global-set-key [C-M-tab] 'clang-format-region)

;;--------------------------------------------------------------- ;; START automatically formatting according to the Google C style prior to saving (defun clang-format-before-save () (interactive) (when (or (eq major-mode 'c++-mode) (eq major-mode 'c-mode)) (clang-format-buffer)))

(add-hook 'before-save-hook 'clang-format-before-save) ;; END automatically formatting according to the Google C style prior to saving ;;---------------------------------------------------------------

;;--------------------------------------------------------------- ;; START allow us to get english language explanations of complex C++ declarations ;; To use, select a declaration such as "char*(*(\*p)[5])(int)", and then type: "C-x cdecl" (defun cdecl () (interactive) (if (eq major-mode 'c++-mode) (progn (interactive) (shell-command (concat "c++decl explain "" (buffer-substring (region-beginning) (region-end)) """))) (progn (interactive) (shell-command (concat "cdecl explain "" (buffer-substring (region-beginning) (region-end)) """))) ) ) ;; END allow us to get english language explanations of complex C++ declarations ;;--------------------------------------------------------------- Setup emacsclient to autospawn the emacs daemon (optional)

Append the following to \~/.bashrc: export ALTERNATE\_EDITOR="" Apply changes: . \~/.bashrc Use as follows: emacsclient -n -c hellworld.cpp Synopsis of our customized emacs shortcuts

C-= Run clang autocomplete C-c s G Jump to global definition of function without prompting (uses cscope) C-c s L Generate a new cscope index C-c s s Find symbol definition under point (using cscope) C-x g t google-this C-x g C-h See all google this keybindings C-x clang-format-region Automatically format the current line or selected region of C/C++ code C-x clang-format-buffer Automatically format the current buffer of C/C++ code NOTE: The .emacs configuration above will automatically format the current C/C++ buffer every time it is saved. Optional add-ons to this C++ dev environment:

Setting up PNaCl C++ development environment on Linux

PNaCl (Portable Native Client) allows you to deploy C++ clients via the Chrome web-browser Setting up emscripten development environment on Linux

emscripten allows you to deploy C++ clients as browser-based javascript applications
