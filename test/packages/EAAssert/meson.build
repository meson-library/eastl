
includes = [include_directories('include'), 
            include_directories('../EABase/include/Common')] 

sources = ['source/eaassert.cpp']

cpp_args +=['-D_CRT_SECURE_NO_WARNINGS', 
            '-D_SCL_SECURE_NO_WARNINGS', 
            '-DEASTL_OPENSOURCE=1', 
            '-DEASTL_THREAD_SUPPORT_AVAILABLE=0']




static_lib_name        = 'EAAssert'
static_lib_name_prefix = []
static_lib_name_suffix = []

if system == 'windows' and cppc_id == 'msvc'  
    static_lib_name       += '_static'
    static_lib_name_prefix = ''
    static_lib_name_suffix = 'lib'
endif

_internal_static_EAAssert = static_library(static_lib_name,
                                           name_prefix         : static_lib_name_prefix, 
                                           name_suffix         : static_lib_name_suffix,
                                           include_directories : includes,
                                           sources             : sources,
                                           cpp_args            : cpp_args, 
                                           link_args           : link_args,
                                           install             : false)
  
_internal_static_EAAssert_dep = declare_dependency(include_directories : includes,
                                            link_with           : _internal_static_EAAssert)