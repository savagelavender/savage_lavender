using HorizonSideRobots
include("lib_robot.il")
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
    end
    function numsteps_along!(robot,side)
        num=0
        while !isborder(robot, side)
            move!(robot,side)
            num+=1
        end
    return num
    end
end
r=robot(animate=true)
####

move_throwborder!

#number1
using HorizonSideRobots
include("librobot.jl")
function crest!(robot)
    for i in sides
        n = 0
        while !isborder(robot, i)
            putmarker!(robot)
            move!(robot, i)
            n += 1
        end
        putmarker!(robot)
        move_step!(robot, n, inverse(i))
    end
end
#number2
using HorizonSideRobots
include("librobot.jl")
function mark_frame_perimetr!(r::Robot) 

    num_vert = moves!(r, Sud)

    for side in sides
        putmarkers!(r, side)
    end

    moves!(r, Nord, num_vert)
end

function moves!(r::Robot, side::HorizonSide)
    n=0
    while isborder(r, side) == false
        move!(r, side)
        n+=1
    end
    return n
end

function moves!(r::Robot, side::HorizonSide, n::Int)
    for _ in 1:n
        move!(r, side)
    end
end

function putmarkers!(r::Robot, side::HorizonSide)
    while isborder(r, side)==false
        move!(r, side)
        putmarker!(r)
    end
end
#number3


