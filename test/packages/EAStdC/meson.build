
lib_name = 'EAStdC'




includes = [include_directories('include'), 
            include_directories('../EABase/include/Common')] 

sources = ['source/EACallback.cpp',
           'source/EACType.cpp',
           'source/EADateTime.cpp',
           'source/EAFixedPoint.cpp',
           'source/EAGlobal.cpp',
           'source/EAHashCRC.cpp',
           'source/EAHashString.cpp',
           'source/EAMemory.cpp',
           'source/EAProcess.cpp',
           'source/EARandom.cpp',
           'source/EAScanf.cpp',
           'source/EAScanfCore.cpp',
           'source/EASprintf.cpp',
           'source/EASprintfCore.cpp',
           'source/EASprintfOrdered.cpp',
           'source/EAStdC.cpp',
           'source/EAStopwatch.cpp',
           'source/EAString.cpp',
           'source/EATextUtil.cpp',
           'source/Int128_t.cpp']

cpp_args +=['-D_CRT_SECURE_NO_WARNINGS', 
            '-D_SCL_SECURE_NO_WARNINGS', 
            '-DEASTL_OPENSOURCE=1', 
            '-DEASTL_THREAD_SUPPORT_AVAILABLE=0']




if lib_type == 'static' or lib_type == 'both' 
    static_lib_name = lib_name

    static_lib_name_prefix = []
    static_lib_name_suffix = []

    if system == 'windows' and cppc_id == 'msvc'  
        static_lib_name       += '_static'
        static_lib_name_prefix = ''
        static_lib_name_suffix = 'lib'
    endif

    _internal_static_EAStdC = static_library(static_lib_name,
                                name_prefix         : static_lib_name_prefix, 
                                name_suffix         : static_lib_name_suffix,
                                include_directories : includes,
                                sources             : sources,
                                cpp_args            : cpp_args, 
                                link_args           : link_args,
                                dependencies        : [_internal_static_EAAssert_dep, _internal_static_EAThread_dep],
                                install             : false)
  
    _internal_static_EAStdC_dep = declare_dependency(include_directories : includes,
                                                     link_with           : _internal_static_EAStdC)
endif

if lib_type == 'shared' or lib_type == 'both'
    shared_lib_name = lib_name

    _internal_shared_EAStdC = shared_library(shared_lib_name, 
                                   include_directories : includes,
                                   sources         : sources,
                                   cpp_args        : cpp_args + ['-DEA_DLL=1', '-DEASTDC_API=__declspec(dllexport)'], 
                                   link_args       : link_args,  
                                   dependencies    : [_internal_static_EAAssert_dep, _internal_shared_EAThread_dep],
                                   install         : true)

    _internal_shared_EAStdC_dep = declare_dependency(include_directories : includes,
                                                     compile_args        : ['-DEA_DLL=1'],
                                                     link_with           : _internal_shared_EAStdC)
endif




if lib_type == 'static'
    _internal_EAStdC_dep = _internal_static_EAStdC_dep
elif lib_type == 'shared' or lib_type == 'both'
    _internal_EAStdC_dep = _internal_shared_EAStdC_dep
endif
