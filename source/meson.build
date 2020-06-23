
includes = [include_directories('../include'), 
            include_directories('../test/packages/EABase/include/Common')]

sources = ['allocator_eastl.cpp',
           'assert.cpp',
           'fixed_pool.cpp',
           'hashtable.cpp',
           'intrusive_list.cpp',
           'numeric_limits.cpp',
           'red_black_tree.cpp',
           'string.cpp',
           'thread_support.cpp']

cpp_args += ['-DEASTL_OPENSOURCE=1', 
             '-D_CRT_SECURE_NO_WARNINGS', 
             '-D_SCL_SECURE_NO_WARNINGS']




if lib_type == 'static' or lib_type == 'both' 
    static_lib_name        = name
    static_lib_name_prefix = []
    static_lib_name_suffix = []

    if system == 'windows' and cppc_id == 'msvc'  
        static_lib_name       += '_static'
        static_lib_name_prefix = ''
        static_lib_name_suffix = 'lib'
    endif

    eastl_static = static_library(static_lib_name,
                                  name_prefix         : static_lib_name_prefix, 
                                  name_suffix         : static_lib_name_suffix,
                                  include_directories : includes,
                                  sources             : sources,
                                  cpp_args            : cpp_args, 
                                  link_args           : link_args,
                                  install             : true)

    eastl_static_dep = declare_dependency(include_directories : includes,
                                          link_with           : eastl_static)
endif

if lib_type == 'shared' or lib_type == 'both'
    shared_lib_name = name 

    eastl_shared = shared_library(shared_lib_name, 
                                  include_directories : includes,
                                  sources             : sources,
                                  cpp_args            : cpp_args + ['-DEA_DLL=1', '-DEASTL_API=__declspec(dllexport)'], 
                                  link_args           : link_args,   
                                  install             : true)

    eastl_shared_dep = declare_dependency(include_directories : includes,
                                          compile_args        : ['-DEA_DLL=1'],
                                          link_with           : eastl_shared)
endif




if lib_type == 'static'
    eastl_dep = eastl_static_dep
elif lib_type == 'shared' or lib_type == 'both'
    eastl_dep = eastl_shared_dep
endif