#using HorizonSideRobots
#include("librobot.jl")
#r = Robot(animate=true)
#function 
#function shatl!(stop_condition::Function, robot; start_side)
    #s = start_side
    #n = 0
    #while stop_condition() == false
        #n += 1
        #move!(()->stop_condition(), robot, s, n)
       
        #s = inverse(s)
    #end
    #return (n+1)÷2 # - число шагов от начального положения до конечного
#end

using HorizonSideRobots
robot = Robot("task7.sit",animate = true)

function move_throughborder!(robot,side_border)
    n = 0
    side = left(side_border)
    while isborder(robot,side_border)
        n += 1
        move_n!(robot,side,n)
        side = inverse_side(side)
    end
    move!(robot,side_border)
    move_n!(robot, side, div((n+1),2))

end


function move_n!(robot, side::HorizonSide, n)
    for x in 1:n
        move!(robot,side)
    end    
end

inverse_side(side::HorizonSide) = HorizonSide(mod(Int(side)+2,4))

left(side::HorizonSide) = HorizonSide(mod(Int(side)+1,4))

move_throughborder!(robot,Nord)

