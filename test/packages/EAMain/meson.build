
lib_name = 'EAMain'




includes = [include_directories('include'), 
            include_directories('../EABase/include/Common'), 
            include_directories('source')] 

sources = ['source/EAEntryPointMain.cpp',
           'source/EAMainExit.cpp',
           'source/EAMainPrint.cpp',
           'source/EAMain.cpp',
           'source/internal/EAMainChannels.cpp',
           'source/internal/EAMainPrintManager.cpp',
           'source/internal/EAMainStartupShutdown.cpp',
           'source/internal/NetworkChannel.cpp']

cpp_args +=['-D_CRT_SECURE_NO_WARNINGS', 
            '-D_SCL_SECURE_NO_WARNINGS', 
            '-DEASTL_OPENSOURCE=1', 
            '-DEASTL_THREAD_SUPPORT_AVAILABLE=0',
            '-DEAMAIN_NETWORK_CHANNEL_PORT=8080']




if lib_type == 'static' or lib_type == 'both' 
    static_lib_name        = lib_name
    static_lib_name_prefix = []
    static_lib_name_suffix = []

    if system == 'windows' and cppc_id == 'msvc'  
        static_lib_name       += '_static'
        static_lib_name_prefix = ''
        static_lib_name_suffix = 'lib'
    endif

    _internal_static_EAMain = static_library(static_lib_name,
                                name_prefix         : static_lib_name_prefix, 
                                name_suffix         : static_lib_name_suffix,
                                include_directories : includes,
                                sources             : sources,
                                cpp_args            : cpp_args, 
                                link_args           : link_args,
                                dependencies        : [_internal_static_EAAssert_dep, _internal_static_EAStdC_dep, _internal_static_EAThread_dep],
                                install             : false)
  
    _internal_static_EAMain_dep = declare_dependency(include_directories : includes,
                                                     link_with           : _internal_static_EAMain)
endif

if lib_type == 'shared' or lib_type == 'both'
    shared_lib_name = lib_name

    _internal_shared_EAMain = shared_library(shared_lib_name, 
                                   include_directories : includes,
                                   sources             : sources,
                                   cpp_args            : cpp_args + ['-DEA_DLL=1', '-DEAMAIN_API=__declspec(dllexport)'], 
                                   link_args           : link_args,  
                                   dependencies        : [_internal_static_EAAssert_dep, _internal_shared_EAStdC_dep, _internal_shared_EAThread_dep],
                                   install             : true)

    _internal_shared_EAMain_dep = declare_dependency(include_directories : includes,
                                                     compile_args        : ['-DEA_DLL=1'],
                                                     link_with           : _internal_shared_EAMain)
endif




if lib_type == 'static'
    _internal_EAMain_dep = _internal_static_EAMain_dep
elif lib_type == 'shared' or lib_type == 'both'
    _internal_EAMain_dep = _internal_shared_EAMain_dep
endif