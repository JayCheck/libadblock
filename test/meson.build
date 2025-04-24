project_root = get_variable('project_root')

project_deps = [
  dependency('gtest'),
  dependency('gtest_main'),
  get_variable('project_dep'),
  get_variable('impl_dep'),
  dependency('stream9_url'),
]

project_inc = [
  include_directories('../include'),
  include_directories('../src'),
]

project_defs = [
  '-DDATA_DIR=' + meson.current_source_dir() / 'data',
  '-DPROJECT_ROOT=' + '"' + project_root + '"',
]

subdir('api')
subdir('core')
subdir('parser')
subdir('rule')
subdir('pattern')
subdir('option')
subdir('index')

test_src = files(
  'reg_dom.cpp',
  'domain_data_base.cpp',
)

test_exe = executable(
  'libadblock_test',
  test_src,
  include_directories: project_inc,
  dependencies: project_deps,
  cpp_args: project_defs,
  link_with: [
    api_lib, core_lib, parser_lib, rule_lib,
    pattern_lib, option_lib, index_lib,
  ],
)

test('libadblock_test', test_exe)

run_target('run',
  command: [test_exe, '--gtest_brief=1'],
)
