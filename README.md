numsteps_along!(robot,side)
function num_markers!(robot):: Integer
  nsteps_sud=nummarkers_along!(robot,sud)
  nsteps_west=numsteps_along!(robot,west)
  num_markers=num_markers!(robot,side)
  while !isborder(nord)
    move!(robot,nord)
    num_markers+=num_markers!(robot,side)
  end
  along(robot,sud)
  along(robot,west)
  move!(robot,ost, nstep_west)
  move!(robot,nord,nstep_sud)
  function num_markers!(robot, side)
    num=ismarker(robot)
    while !isborder(robot,side)
      move!(robot,side)
      if ismarker(robot)
        num+=1
      end
    end
    return num
    funcnion numsteps_along!(robot,side)
      num=0
      while !isborder(robot, side)
        move!(robot,side)
        num+=1
      end
      return num
    end
