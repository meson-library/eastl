
includes = [include_directories('.'), 
            include_directories('../packages/EABase/include/Common')] 

sources = ['EASTLTest.cpp','EASTLTestAllocator.cpp', 'main.cpp', 'TestAlgorithm.cpp', 
           'TestAllocator.cpp', 'TestAny.cpp', 'TestArray.cpp', 'TestBitset.cpp', 
           'TestBitVector.cpp', 'TestCharTraits.cpp', 'TestChrono.cpp', 'TestCppCXTypeTraits.cpp', 
           'TestDeque.cpp', 'TestExtra.cpp', 'TestFinally.cpp', 'TestFixedFunction.cpp', 
           'TestFixedHash.cpp', 'TestFixedList.cpp', 'TestFixedMap.cpp', 'TestFixedSet.cpp', 
           'TestFixedSList.cpp', 'TestFixedString.cpp', 'TestFixedTupleVector.cpp', 'TestFixedVector.cpp', 
           'TestFunctional.cpp', 'TestHash.cpp', 'TestHeap.cpp', 'TestIntrusiveHash.cpp', 
           'TestIntrusiveList.cpp', 'TestIntrusiveSDList.cpp', 'TestIntrusiveSList.cpp', 'TestIterator.cpp', 
           'TestList.cpp', 'TestListMap.cpp', 'TestLruCache.cpp', 'TestMap.cpp', 
           'TestMemory.cpp', 'TestMeta.cpp', 'TestNumericLimits.cpp', 'TestOptional.cpp', 
           'TestRandom.cpp', 'TestRatio.cpp', 'TestRingBuffer.cpp', 'TestSegmentedVector.cpp', 
           'TestSet.cpp', 'TestSList.cpp', 'TestSmartPtr.cpp', 'TestSort.cpp', 
           'TestSpan.cpp', 'TestSparseMatrix.cpp', 'TestString.cpp', 'TestStringHashMap.cpp', 
           'TestStringMap.cpp', 'TestStringView.cpp', 'TestTuple.cpp', 'TestTupleVector.cpp', 
           'TestTypeTraits.cpp', 'TestUtility.cpp', 'TestVariant.cpp', 'TestVector.cpp', 
           'TestVectorMap.cpp', 'TestVectorSet.cpp']

cpp_args +=['-D_CRT_SECURE_NO_WARNINGS', 
            '-D_SCL_SECURE_NO_WARNINGS', 
            '-DEASTL_OPENSOURCE=1', 
            '-DEASTL_THREAD_SUPPORT_AVAILABLE=0']           




EASTLTest = executable('EASTLTest',
                       include_directories : includes,
                       sources             : sources,
                       cpp_args            : cpp_args + ['-std:c++17'], 
                       dependencies        : [eastl_dep, _internal_static_EAAssert_dep, _internal_EAStdC_dep, _internal_EAThread_dep, _internal_EAMain_dep, _internal_EATest_dep],
                       install             : true)


 