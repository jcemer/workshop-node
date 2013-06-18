flour = require 'flour'

task 'build', ->
    compile 'styles/main.styl', 'styles/main.css'

task 'watch', ->
    invoke 'build'
    watch 'styles/*', -> invoke 'build'