# This file is used to compile grftool.
# You need scons: http://www.scons.org/
# Type 'scons -Q' in the commandline to compile grftool.

import string
import subprocess

DEBUG = ARGUMENTS.get('DEBUG', 0);
CC = ARGUMENTS.get('CC', None);
CXX = ARGUMENTS.get('CXX', None);

PREFIX = ARGUMENTS.get('PREFIX', '/usr/local')
BINDIR = ARGUMENTS.get('BINDIR', PREFIX + '/bin')
DATADIR = ARGUMENTS.get('DATADIR', PREFIX + '/share')
PKGDATADIR = ARGUMENTS.get('PKGDATADIR', DATADIR + '/grftool')

env = Environment(
	CCFLAGS=Split('-Wformat -Wformat-security -Wparentheses -Wunused-variable -Wuninitialized -Wall -W -Wundef -Wpointer-arith -Wcast-align -Wno-unused-parameter -O2 -g'), # -Wconversion -Wcast-qual
	CPPPATH=['.'],
	LINKFLAGS='')
if CC != None:
	env['CC'] = CC
if CXX != None:
	env['CXX'] = CXX

env.Decider('MD5-timestamp')

conf = env.Configure()
env = conf.Finish()

Export('env')
Export('DEBUG')
Export('BINDIR')

# Run sub SConscripts
SConscript('lib/SConscript', build_dir='lib/static', duplicate=False)

SConscript('tools/SConscript')

#env.Alias('install', [BINDIR, DATADIR + '/applications', PKGDATADIR])
