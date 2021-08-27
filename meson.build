project('imgui', 'cpp')

compiler = meson.get_compiler('cpp')
link_deps = [
    dependency('sdl2'),
    dependency('glad'),
    dependency('stb'),
]

incdirs = ['.', 'backends']
cflags = []

opengl = get_option('opengl')

if opengl == 'angle'
    cflags += ['-DOPENGL_PROFILE=2']
else
    cflags += ['-DOPENGL_PROFILE=1']
endif

sources = [
    'imgui.cpp',
    'imgui_demo.cpp',
    'imgui_draw.cpp',
    'imgui_tables.cpp',
    'imgui_widgets.cpp',
    'backends/imgui_impl_opengl3.cpp',
    'backends/imgui_impl_sdl2.cpp',
]

incdirs = include_directories(incdirs)

imgui = static_library(
    'imgui',
    sources,
    cpp_args: cflags,
    include_directories: incdirs,
    dependencies: link_deps,
)
imgui_dep = declare_dependency(
    include_directories: incdirs,
    dependencies: link_deps,
    link_with: imgui,
    version: meson.project_version()
)

meson.override_dependency('imgui', imgui_dep)

# vim: set ts=4 sts=4 sw=4 et:
