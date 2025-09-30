# SPDX-License-Identifier: LGPL-2.1-or-later

vcs_tag = get_option('vcs-tag')
mode = get_option('mode')

version_h = custom_target('version',
    build_always_stale : vcs_tag == true,
    input : project_root / 'src/version/version.h.in',
    output : 'version.h',
    capture : true,
    install : true,
    install_dir : get_option('includedir') / 'systemd',
    command : [
        project_root / 'tools/vcs-tag.sh',
        '@INPUT@',
        mode,
        vcs_tag ? '1' : '0',
    ],
)

version_include = include_directories('.')

# Make sure userspace_sources exists
userspace_sources = get_variable('userspace_sources', [])
userspace_sources += version_h
