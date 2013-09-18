require 'rake'

desc "point the revealjs server at a particular lesson number"
task :point_to, :number do |t, number|
  lesson = determine_lesson_dir(number[:number])
  puts "Updating reveal.js to point to lesson #{lesson}"
  `rm -f revealjs/slides`
  slides_ln = `ls ../BEWD_Curriculum | grep #{lesson}_*`.chop!
  `ln -s ../../BEWD_Curriculum/#{slides_ln}/slides revealjs/slides`
end

namespace :g do
  desc "starts the revealjs server"
  task :start do
    exec 'cd revealjs && grunt serve'
  end

  desc "stops the revealjs server"
  task :stop do
    `ps aux | grep grunt | grep -v grep | awk '{print $2}' | xargs kill`
  end
end

def determine_lesson_dir number
  number.size == 1 ? "0#{number}" : number
end
