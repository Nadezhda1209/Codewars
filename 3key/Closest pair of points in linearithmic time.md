[Closest pair of points in linearithmic time](https://www.codewars.com/kata/5376b901424ed4f8c20002b7)


DESCRIPTION:
```
Given a number of points on a plane, your task is to find two points with the smallest distance between them in linearithmic O(n log n) time.

Example
  1  2  3  4  5  6  7  8  9
1  
2    . A
3                . D
4                   . F       
5             . C
6              
7                . E
8    . B
9                   . G
For the plane above, the input will be:

(
  (2,2), # A
  (2,8), # B
  (5,5), # C
  (6,3), # D
  (6,7), # E
  (7,4), # F
  (7,9)  # G
)
=> closest pair is: ((6,3),(7,4)) or ((7,4),(6,3))
(both answers are valid. You can return a list of tuples too)
The two points that are closest to each other are D and F.
Expected answer should be an array with both points in any order.

Goal
The goal is to come up with a function that can find two closest points for any arbitrary array of points, in a linearithmic time.

Note: Don't use math.hypot, it's too slow...
```
SOLUTION:
```
import math
from operator import itemgetter
def closest_pair(Point):
# Решить расстояние между двумя точками
    def Distance(a_point, b_point):
        return math.sqrt((a_point[0]-b_point[0])**2 + (a_point[1]-b_point[1])**2)

    # Метод грубой силы для нахождения расстояния между ближайшими двумя точками
    def ClosePoints(Points_X, leftindex, rightindex):
        mindist = math.inf
        close_points = []
        for i in range(leftindex, rightindex+1):
            for j in range(i+1, rightindex+1):
                distance = Distance(Points_X[i], Points_X[j])
                if distance < mindist:
                    # Очищать список каждый раз перед сохранением информации о последних двух точках
                    close_points.clear()
                    mindist = distance
                    # Сохраняем информацию о последних двух точках
                    close_points.append(Points_X[i])
                    close_points.append(Points_X[j])
        return mindist, close_points


    def ClosePoints11(Points_X, Point_Y, leftindex, rightindex):
        left_Points_Y = []
        right_Point_Y = []
        Point_Y_temp = []

        if (rightindex-leftindex+1) <= 3:   # Если точек меньше 4, напрямую использовать грубую силу для решения
            distance, close_points = ClosePoints(Points_X, leftindex, rightindex)
            return distance, close_points

        midindex = int((leftindex+rightindex)/2)    # Найдите среднюю позицию
        for i in range(len(Point_Y)):       # Разделить Points_y на левую и правую части
            if Point_Y[i][0] < Points_X[midindex][0]:
                left_Points_Y.append(Point_Y[i])
            else:
                right_Point_Y.append(Point_Y[i])
        distance1, close_points1 = ClosePoints11(Points_X, left_Points_Y, leftindex, midindex)
        distance2, close_points2 = ClosePoints11(Points_X, right_Point_Y, midindex+1, rightindex)
        if distance1 < distance2:
            min_distance = distance1
            close_points = close_points1
        else:
            min_distance = distance2
            close_points = close_points2

        # Найдите минимальное расстояние в средней части
        for i in range(len(Point_Y)):   # b Скопируйте подмножество полосы шириной 2 * d посередине в Point_Y_temp
            if math.fabs(Point_Y[i][0]-Points_X[midindex][0]) <= min_distance:
                Point_Y_temp.append(Point_Y[i])

        # Находим ближайшую точку в Point_Y_temp
        distance3 = math.inf
        close_points3 = []
        for i in range(len(Point_Y_temp)):
            for j in range(i+1, len(Point_Y_temp)):
                if (Point_Y_temp[j][1]-Point_Y_temp[i][1]) >= min_distance:
                    break
                temp_dis = Distance(Point_Y_temp[i], Point_Y_temp[j])
                if temp_dis < distance3:
                    distance3 = temp_dis
                    close_points3.clear()
                    close_points3.append(Point_Y_temp[i])
                    close_points3.append(Point_Y_temp[j])
        if min_distance > distance3:
            d = distance3
            close_points = close_points3
        else:
            d = min_distance
        return d, close_points


    def ClosePoints1(Point, leftindex, rightindex):
        #print('Перед сортировкой:', Point)
        Point_X = Point
        Point_X = sorted(Point_X)
        #print('После сортировки по координате X:', Point_X)
        Point_Y = Point
        Point_Y = sorted(Point_Y, key=itemgetter(1))
        #print('После сортировки по координате Y:', Point_Y)
        return ClosePoints11(Point_X, Point_Y, leftindex, rightindex)

    if __name__ == '__main__':
        Point = list(points)
    mindist, close_points = ClosePoints1(Point, 0, len(Point)-1)
    return(tuple(close_points))
    pass
```