flour = require 'flour'
cp    = require 'child_process'

task 'build', ->
    compile 'styles/main.styl', 'styles/main.css'

task 'watch', ->
    invoke 'build'
    watch 'styles/*', -> invoke 'build'

task 'deploy', ->
    cp.exec "git status", (err, stdout) ->
        unless stdout.indexOf("nothing to commit") >= 0
            console.error "Please stash or commit your changes before deploy."
            return

        child = cp.exec """
            git checkout gh-pages &&
            git merge -s recursive -X theirs master &&
            cake build &&
            git add . &&
            git commit --allow-empty -m "Regenerate" &&
            git push -f origin gh-pages &&
            git checkout master
        """
        child.stdout.pipe process.stdout
        child.stderr.pipe process.stderr
