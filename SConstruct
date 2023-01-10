import os, subprocess, platform, sys

libs_path = [
            '/home/randys/src/games/godot-cpp/bin'
            ]

libs =  [
        'libgodot-cpp.linux.debug.64.a',
        'libgodot-cpp.linux.release.64.a'
        #'libgodot-cpp.windows.Release.lib'
        ]

include_path =  [
                "/home/randys/src/games/godot-cpp/godot-headers/",
                "/home/randys/src/games/godot-cpp/include/",
                "/home/randys/src/games/godot-cpp/include/core/",
                "/home/randys/src/games/godot-cpp/include/gen/"
                ]

env = Environment(CPPPATH = include_path, LIBS = libs[0], LIBPATH=libs_path)

opts = Variables([],ARGUMENTS)
opts.Add(EnumVariable
            (
                'target','Compilation target', 'release', 
                allowed_values=('debug','release'),
                ignorecase = 2
            )                     
        )

opts.Update(env)

if env['target'] == 'debug':
    #env.Append(CCFLAGS = '-W')
    env.Append(CCFLAGS = '-MD')
    #env.Append(CCFLAGS = '-Z')
    #env.Append(CCFLAGS = '-EHsc')
    env.Append(CCFLAGS = '-DNDEBUG')
    #env.Append(CCFLAGS = '-FS')
    

    Mkdir('godot/native')
    env.SharedLibrary(target='godot/native/gdns_lib-D', source=Glob('src/*.cpp'), INCLUDE = include_path, LIBS = libs[0], LIBPATH = libs_path)
    
else:
    env.Append(CCFLAGS = '/W3')
    env.Append(CCFLAGS = '/MD')
    env.Append(CCFLAGS = '/Zi')
    env.Append(CCFLAGS = '/Ox')
    env.Append(CCFLAGS = '/EHsc')
    env.Append(CCFLAGS = '/DNDEBUG')
    env.Append(CCFLAGS = '/FS')

    Mkdir('godot/native')
    env.SharedLibrary(target='godot/native/gdns_lib-R', source=Glob('src/*.cpp'), INCLUDE = include_path, LIBS = libs[1], LIBPATH = libs_path)




