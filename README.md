def rectangle_fill(length,width,color,x=0,y=0):#先向上画宽度边
    p.up()
    p.goto(x,y)#长方形左下角起始点
    p.down()
    p.left(90)#笔尖向上，画宽度边
    p.color(color)
    p.begin_fill()
    for i in range(2):
        p.forward(width)
        p.right(90)
        p.forward(length)
        p.right(90)
    p.end_fill()
    p.right(90)#笔尖回归向右
    return
def bigstar_fill(side_length,color,x=0,y=0):
    p.up()
    p.goto(x,y)#五角星左顶点起始点
    p.down()
    p.color(color)
    p.begin_fill()
    for i in range(5):
        p.forward(side_length)
        p.right(144)
    p.end_fill()
    return
def smallstar_fill(side_length,radius,color,left_angle = 0,right_angle=0,x=0,y=0):
    p.up()
    p.left(left_angle)#left_ange是小五角星相对于大五角星的角度
    p.forward(radius)#大五角星左顶点到小五角星左顶点距离
    p.down()
    p.color(color)
    p.right(right_angle)#right_angle是小五角星的起始角度
    p.begin_fill()
    for i in range(5):
        p.forward(side_length)
        p.right(144)
    p.end_fill()
    p.left(right_angle - left_angle)#笔尖回归向右
    p.up()
    p.goto(x,y)#回到大五角星左顶点
    p.down()
    return
def main():
    rectangle_fill(300,200,'red',-200,-100)
    bigstar_fill(60,'yellow',-160,50)
    radius = [85,95,95,85]#大五角星左顶点到小五角星左顶点距离
    left_angle = [22, 8, -8, -22]#left_ange是小五角星相对于大五角星的角度
    right_angle = [52, 50, -8, 0]#right_angle是小五角星的起始角度
    for i in range(4):
        smallstar_fill(15,radius.pop(0),'yellow',left_angle.pop(0),right_angle.pop(0),-160,50)
    p.up()
    #p.goto(-130,40)#将画笔藏于大五角星内
    p.goto(-200,-100)
    p.left(90)
    p.pensize(10)
    p.color('black')
    p.down()
    p.backward(150)
    p.forward(350)
    p.backward(50)
    return
import turtle
p = turtle.Pen()
main()
    
