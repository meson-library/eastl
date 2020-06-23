
includes = [include_directories('.'), 
            include_directories('../../test/packages/EABase/include/Common'), 
            include_directories('../../test/source')] 

sources = ['BenchmarkAlgorithm.cpp', 'BenchmarkBitset.cpp', 'BenchmarkDeque.cpp',
           'BenchmarkHash.cpp','BenchmarkHeap.cpp','BenchmarkList.cpp',
           'BenchmarkMap.cpp','BenchmarkSet.cpp','BenchmarkSort.cpp',
           'BenchmarkString.cpp','BenchmarkTupleVector.cpp','BenchmarkVector.cpp',
           'EASTLBenchmark.cpp', '../../test/source/EASTLTest.cpp', '../../test/source/EASTLTestAllocator.cpp',
           'main.cpp']

cpp_args +=['-D_CRT_SECURE_NO_WARNINGS', 
            '-D_SCL_SECURE_NO_WARNINGS', 
            '-DEASTL_OPENSOURCE=1', 
            '-DEASTL_THREAD_SUPPORT_AVAILABLE=0']           




EASTLBenchmarks = executable('EASTLBenchmarks',
                             include_directories : includes,
                             sources             : sources,
                             cpp_args            : cpp_args + ['-std:c++17'], 
                             dependencies        : [eastl_dep, _internal_static_EAAssert_dep, _internal_EAStdC_dep, _internal_EAThread_dep, _internal_EAMain_dep, _internal_EATest_dep],
                             install             : true)