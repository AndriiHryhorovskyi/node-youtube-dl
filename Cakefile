{spawn, exec} = require('child_process')

execcb = (err, stdout, stderr) ->
  throw err if err

datacb = (data) ->
  console.log data.toString().replace /\s+$/, ''

task 'build', 'Build project from src/*.coffee to lib/*.js', ->
  exec 'coffee -o lib -c src', execcb
  exec 'coffee -c scripts', execcb

task 'watch', 'Build and watch for changes', ->
  child = spawn 'coffee', ['-w', '-o', 'lib', '-c', 'src']
  child.stdout.on 'data', datacb
  child.stderr.on 'data', datacb
