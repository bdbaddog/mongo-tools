# -*- mode:python; coding:utf-8; -*-

vars = Variables('custom.py')
vars.Add(ListVariable('GOTAGS', 'Set GOTAGS', [],
                    ['ssl', 'sasl']))

env=Environment(variables = vars)
Help(vars.GenerateHelpText(env))


env['GOPATH'] = ['/media/sf_mongodb/mongo-tools/.gopath', '/media/sf_mongodb/mongo-tools/vendor']
env['GOFLAGS'] = ' -x '
env['GO'] = '/usr/local/go/bin/go'
# env.AppendENVPath('PATH','/home/bdbaddog/tools/mongodbtoolchain/v2/bin')
env.Tool('scons-gobuilder',toolpath=['/media/sf_mongodb/'])


# env.goObject('src/ex3/hello-world.go')

env.goProgram('bin/mongoimport',['mongoimport/main/mongoimport.go',])

print(env.Dump('ENV'))
for f in env._dict.keys():
    if f.startswith('GO'):
        print("%s->%s"%(f,env[f]))


# x=FindPathDirs('GOPATH')
#
# for p in x(env):
#     print("-->%s"%p)

