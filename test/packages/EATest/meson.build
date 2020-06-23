
lib_name = 'EATest'




includes = [include_directories('include'), 
            include_directories('../EABase/include/Common')] 

sources = ['source/EATest.cpp']

cpp_args +=['-D_CRT_SECURE_NO_WARNINGS', 
            '-D_SCL_SECURE_NO_WARNINGS', 
            '-DEASTL_OPENSOURCE=1', 
            '-DEASTL_THREAD_SUPPORT_AVAILABLE=0']




if lib_type == 'static' or lib_type == 'both' 
    static_lib_name        = lib_name
    static_lib_name_prefix = []
    static_lib_name_suffix = []

    if system == 'windows' and cppc_id == 'msvc'  
        static_lib_name       += '_static'
        static_lib_name_prefix = ''
        static_lib_name_suffix = 'lib'
    endif

    _internal_static_EATest = static_library(static_lib_name,
                                             name_prefix         : static_lib_name_prefix, 
                                             name_suffix         : static_lib_name_suffix,
                                             include_directories : includes,
                                             sources             : sources,
                                             cpp_args            : cpp_args, 
                                             link_args           : link_args,
                                             dependencies        : [eastl_static_dep, _internal_static_EAAssert_dep, _internal_static_EAStdC_dep, _internal_static_EAThread_dep, _internal_static_EAMain_dep],
                                             install             : false)
  
    _internal_static_EATest_dep = declare_dependency(include_directories : includes,
                                                     link_with           : _internal_static_EATest)
endif

if lib_type == 'shared' or lib_type == 'both'
    shared_lib_name        = lib_name

    _internal_shared_EATest = shared_library(shared_lib_name, 
                                             include_directories : includes,
                                             sources             : sources,
                                             cpp_args            : cpp_args + ['-DEA_DLL=1', '-DEATEST_API=__declspec(dllexport)'], 
                                             link_args           : link_args,  
                                             dependencies        : [eastl_shared_dep, _internal_static_EAAssert_dep, _internal_shared_EAStdC_dep, _internal_shared_EAThread_dep, _internal_shared_EAMain_dep],
                                             install             : true)

    _internal_shared_EATest_dep = declare_dependency(include_directories : includes,
                                                     compile_args        : ['-DEA_DLL=1'],
                                                     link_with           : _internal_shared_EATest)
endif




if lib_type == 'static'
    _internal_EATest_dep = _internal_static_EATest_dep
elif lib_type == 'shared' or lib_type == 'both'
    _internal_EATest_dep = _internal_shared_EATest_dep
endif