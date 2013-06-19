flour = require 'flour'
cp    = require 'child_process'

task 'build', ->
    compile 'styles/main.styl', 'styles/main.css'

task 'watch', ->
    invoke 'build'
    watch 'styles/*', -> invoke 'build'

task 'deploy', ->
    cp.exec """
        npm install
        cake build
        git stash
        git checkout gh-pages
        git rebase master
        git add .
        git commit -m "Regenerate"
        git push fork gh-pages
        git checkout master
        git stash pop
    """.split(/\n/).join(' && '), (err, stdout, stderr) ->
        console.error err if err
        console.log stdout
        console.log stderr