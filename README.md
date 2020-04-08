

$ rfnocmodtool newmod xprtest
$ cd rfnoc-xprtest
$ rfnocmodtool add gain
Enter all argument setting "No = N" except of Device ID (1111222233334444).
Default Skeletone code is generated. Refer to follow tree structure.
There is no *.xpr and vivado related files.


rr@rr:~/rfnoc/src/rfnoc-xprtest$ tree -L 4
.
├── apps
│   └── CMakeLists.txt
├── cmake
│   ├── cmake_uninstall.cmake.in
│   └── Modules
│       ├── CMakeParseArgumentsCopy.cmake
│       ├── ettusConfig.cmake
│       ├── FindCppUnit.cmake
│       ├── Findfpga.cmake
│       ├── FindGnuradioRuntime.cmake
│       ├── GrMiscUtils.cmake
│       ├── GrPlatform.cmake
│       ├── GrPython.cmake
│       ├── GrSwig.cmake
│       ├── GrTest.cmake
│       ├── UseSWIG.cmake
│       └── xprtestConfig.cmake
├── CMakeLists.txt
├── docs
│   ├── CMakeLists.txt
│   ├── doxygen
│   │   ├── CMakeLists.txt
│   │   ├── Doxyfile.in
│   │   ├── Doxyfile.swig_doc.in
│   │   ├── doxyxml
│   │   │   ├── base.py
│   │   │   ├── doxyindex.py
│   │   │   ├── generated
│   │   │   ├── __init__.py
│   │   │   └── text.py
│   │   ├── other
│   │   │   ├── group_defs.dox
│   │   │   └── main_page.dox
│   │   └── swig_doc.py
│   └── README.xprtest
├── examples
│   └── README
├── grc
│   ├── CMakeLists.txt
│   └── xprtest_gain.xml
├── include
│   └── xprtest
│       ├── api.h
│       ├── CMakeLists.txt
│       ├── gain_block_ctrl.hpp
│       └── gain.h
├── lib
│   ├── CMakeLists.txt
│   ├── gain_block_ctrl_impl.cpp
│   ├── gain_impl.cc
│   ├── gain_impl.h
│   ├── qa_xprtest.cc
│   ├── qa_xprtest.h
│   └── test_xprtest.cc
├── MANIFEST.md
├── python
│   ├── build_utils_codes.py
│   ├── build_utils.py
│   ├── CMakeLists.txt
│   └── __init__.py
├── README.md
├── rfnoc
│   ├── blocks
│   │   ├── CMakeLists.txt
│   │   └── gain.xml
│   ├── fpga-src
│   │   ├── Makefile.srcs
│   │   └── noc_block_gain.v
│   └── testbenches
│       ├── CMakeLists.txt
│       └── noc_block_gain_tb
│           ├── CMakeLists.txt
│           ├── Makefile
│           └── noc_block_gain_tb.sv
└── swig
    ├── CMakeLists.txt
    └── xprtest_swig.i

20 directories, 57 files
# rfnoc_xprtest
vivado project source tree check
