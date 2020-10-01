

bool isInside(Point polygon[], int n, Point p)
{

    if (n < 3)  return false;


    Point extreme = {INF, p.y};


    int count = 0, i = 0;
    do
    {
        int next = (i+1)%n;

        if (doIntersect(polygon[i], polygon[next], p, extreme))
        {

            if (orientation(polygon[i], p, polygon[next]) == 0)
               return onSegment(polygon[i], p, polygon[next]);

            count++;
        }
        i = next;
    } while (i != 0);


    return count&1;
}


int main()
{
    Point polygon1[] = {{1,0}, {8,3}, {8,8}, {1,5}};
    int n = sizeof(polygon1)/sizeof(polygon1[0]);
    Point p = {3,5};
    isInside(polygon1, n, p)? cout << "True \n": cout <<"False \n";

    Point polygon2[]={{-3,2},{-2,-0.8},{0,1.2},{2.2,0},{2,4.5}};
    int n1=sizeof(polygon2)/sizeof(polygon2[0]);
    Point p1={0,0};
    isInside(polygon2,n1,p1)? cout << "True \n" : cout<<"False \n";
}
