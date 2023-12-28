using HorizonSideRobots
r = Robot(animate = true)
 
function goandmark!(r, Side)
    while !isborder(r, Side)
        putmarker!(r)
        move!(r, Side)
    end
end
 
 
function task2!(r)
	#Side1 = Nord
	#Side2 = East
	#Side3 = Sud 
	#Side4 = West
    a = 0
    b = 0
    while !isborder(r, Nord)
        move!(r, Nord)
        a += 1
    end
    while !isborder(r, East)
        move!(r, East)
        b += 1
    end
    goandmark!(r, Sud)
    goandmark!(r, West)
    goandmark!(r, Nord)
    goandmark!(r, East)
    while a != 0
        move!(r, Sud)
        a -= 1
    end
    while b != 0
        move!(r, East)
        b -= 1
    end
end
