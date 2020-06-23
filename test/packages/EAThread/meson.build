
lib_name = 'EAThread'




includes = [include_directories('include'), 
            include_directories('../EABase/include/Common')] 

sources = ['source/version.cpp',
           'source/eathread_thread.cpp',
           'source/eathread_storage.cpp',
           'source/eathread_semaphore.cpp',
           'source/eathread_rwmutex_ip.cpp',
           'source/eathread_rwmutex.cpp',
           'source/eathread_pool.cpp',
           'source/eathread_mutex.cpp',
           'source/eathread_futex.cpp',
           'source/eathread_condition.cpp',
           'source/eathread_callstack.cpp',
           'source/eathread_barrier.cpp',
           'source/eathread.cpp']

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

    _internal_static_EAThread = static_library(static_lib_name,
                                               name_prefix         : static_lib_name_prefix, 
                                               name_suffix         : static_lib_name_suffix,
                                               include_directories : includes,
                                               sources             : sources,
                                               cpp_args            : cpp_args, 
                                               link_args           : link_args,
                                               install             : false)
  
    _internal_static_EAThread_dep = declare_dependency(include_directories : includes,
                                                       link_with           : _internal_static_EAThread)
endif

if lib_type == 'shared' or lib_type == 'both'
    shared_lib_name = lib_name

    _internal_shared_EAThread = shared_library(shared_lib_name, 
                                               include_directories : includes,
                                               sources             : sources,
                                               cpp_args            : cpp_args + ['-DEA_DLL=1', '-DEATHREADLIB_API=__declspec(dllexport)'], 
                                               link_args           : link_args,  
                                               install             : true)

    _internal_shared_EAThread_dep = declare_dependency(include_directories : includes,
                                                       compile_args        : ['-DEA_DLL=1'],
                                                       link_with           : _internal_shared_EAThread)
endif




if lib_type == 'static'
    _internal_EAThread_dep = _internal_static_EAThread_dep
elif lib_type == 'shared' or lib_type == 'both'
    _internal_EAThread_dep = _internal_shared_EAThread_dep
endif