# -*- mode:python; coding:utf-8; -*-

vars = Variables('custom.py')
vars.Add(ListVariable('GOTAGS', 'Set GOTAGS', [],
                    ['ssl', 'sasl']))

env=Environment(variables = vars)
Help(vars.GenerateHelpText(env))


tool_list = ['bsondump', 'mongostat', 'mongofiles', 'mongoexport',
             'mongoimport', 'mongorestore', 'mongodump', 'mongotop', 'mongooplog',
             ]

conf = Configure(env)
if conf.CheckHeader('pcap.h'):
    tool_list.append('mongoreplay')
else:
    print 'Did not find pcap.h, skipping mongoreplay!'

env = conf.Finish()

env['GOPATH'] = ['/media/sf_mongodb/mongo-tools/.gopath', '/media/sf_mongodb/mongo-tools/vendor']
env['GOFLAGS'] = ' -x '
env['GO'] = '/usr/local/go/bin/go'


env.Tool('scons-gobuilder',toolpath=['/media/sf_mongodb/'])


for tool in tool_list:
    env.goProgram('bin/%s'%tool,['%s/main/%s.go'%(tool,tool),])

# print(env.Dump('ENV'))
# for f in env._dict.keys():
#     if f.startswith('GO'):
#         print("%s->%s"%(f,env[f]))


# x=FindPathDirs('GOPATH')
#
# for p in x(env):
#     print("-->%s"%p)

