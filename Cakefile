flour = require 'flour'
cp    = require 'child_process'

task 'build', ->
    compile 'styles/main.styl', 'styles/main.css'

task 'watch', ->
    invoke 'build'
    watch 'styles/*', -> invoke 'build'

task 'deploy', ->
    child = cp.exec """
        git stash &&
        git checkout gh-pages &&
        git merge master &&
        cake build &&
        git add . &&
        git commit --allow-empty -m "Regenerate" &&
        git push -f origin gh-pages &&
        git checkout master &&
        git stash pop
    """
    child.stdout.pipe process.stdout
    child.stderr.pipe process.stderr
