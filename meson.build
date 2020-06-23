project('eastl', ['cpp'], 
         version       : '3.16.07',  
         license       : ['BSD3'],
         meson_version : '>= 0.49.0')




name = 'eastl'




system     = build_machine.system()
cpu        = build_machine.cpu()
cpu_family = build_machine.cpu_family()

cppc    = meson.get_compiler('cpp')
cppc_id = cppc.get_id() 

lib_type    = get_option('default_library')

includes  = []
sources   = []
cpp_args    = []
link_args = []




if system not in ['windows']
    error('Script (meson.build) not prepared for your platform yet.')
endif

if system == 'windows' and cppc_id not in ['msvc']
    error('Script (meson.build) not prepared for your compiler yet.')
endif




subdir('source')

if get_option('build_test') or get_option('build_benchmark')
	if not meson.is_subproject()
		subdir('test/packages')
	else
		warning('The options ' + name + ':' + 'build_test or build_benchmark' + ' not work in subproject.')
	endif
endif

if get_option('build_test')
	if not meson.is_subproject()
		subdir('test')
	else
		warning('The option ' + name + ':' + 'build_test' + ' not work in subproject.')
	endif
endif

if get_option('build_benchmark')
	if not meson.is_subproject()
		subdir('benchmark')
	else
		warning('The option ' + name + ':' + 'build_benchmark' + ' not work in subproject.')
	endif
endif




install_subdir('include/EASTL', 
			   install_dir : 'include')

install_subdir('doc', 
 			   strip_directory : true, 
			   install_dir     : 'share/docs/eastl')

install_data(['LICENSE', 
			  '3RDPARTYLICENSES.TXT'],
               rename : ['LICENSE.BSD3', 
			             '3RDPARTYLICENSES.TXT'],
               install_dir :  'share/licenses/eastl')
