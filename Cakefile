flour = require 'flour'

task 'build', ->
    compile 'style.styl', 'style.css'

task 'watch', ->
    invoke 'build'
    watch 'style.styl', -> invoke 'build'