package softwaretesting;

public class Triangle
{
private static int Scalene_TRIANGLE = 0;
private static int ISOSCELES_TRIANGLE  = 1;
private static int EQUILATERAL_TRIANGEL = 2;
private static int ERROR_CODE = -1;
public int getNormalTriangle()
{
return Scalene_TRIANGLE;
}
public int getIsoscelesTriangle()
{
return ISOSCELES_TRIANGLE;
}
public int getEquilateralTriangle()
{
return EQUILATERAL_TRIANGEL;
}
public int getErrorCode()
{
return ERROR_CODE;
}
public int judgeType(int a,int b,int c)
{
if ((a<=0)||(b<=0)||(c<=0))
{
return ERROR_CODE;
}
if ((a+b<c || Math.abs(a-b)>c) || (b+c<a || Math.abs(b-c)>a) || (a+c<b || Math.abs(a-c)>b))
{
return ERROR_CODE;
}
if (a==b || b==c || c==a)
{
if (a==b && b==c)
{
return EQUILATERAL_TRIANGEL;
}
else
{
return ISOSCELES_TRIANGLE;
}
}
else
{
return Scalene_TRIANGLE;
}
}
}


package softwaretesting;

import static org.junit.Assert.*;
import org.junit.After;
import org.junit.Before;
import org.junit.Test;
public class Triangletest {
private static Triangle Triangle = new Triangle();
@Before
public void setUp() throws Exception {
}
@Test
public void testIsScaleneTriangle() throws Exception {
assertEquals(Triangle.getNormalTriangle(),Triangle.judgeType(3, 4, 5));
}
@Test
public void testIsIsoscelesTriangle() throws Exception {
assertEquals(Triangle.getIsoscelesTriangle(),Triangle.judgeType(2, 2, 3));
}
@Test
public void testEquilateralTriangle() throws Exception {
assertEquals(Triangle.getEquilateralTriangle(),Triangle.judgeType(2, 2, 2));
}
@Test
public void testNotTriangle() throws Exception {
assertEquals(Triangle.getErrorCode(),Triangle.judgeType(10, -10, 10));
assertEquals(Triangle.getErrorCode(),Triangle.judgeType(10, 2, 2));
}
@After
public void tearDown() throws Exception {
}
}
