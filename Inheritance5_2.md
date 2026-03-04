# Inheritance 5.2
## Course Class
``` java
public class Course {
    private String courseNumber;
    private String courseTitle;
    public void setCourseNumber(String c){
        courseNumber = c;
    }
    public void setCourseTitle(String t){
        courseTitle = t;

    }
    public String getCourseNumber(){
        return courseNumber;
    }
    public String getCourseTitle() {
        return courseTitle;
    }
    public void printInfo(){
        System.out.println("Course Information:");
        System.out.println("    Course Number: " + courseNumber);
        System.out.println("    Course Title: " + courseTitle);
    }
}


```
## Offered Course that extends Course 
``` java
public class OfferedCourse extends Course{
    private String name;
    private String location;
    private String time;
    public void setName(String s){
        name = s;
    }
    public void setLocation(String s) {
        location = s;
    }
    public void setTime(String s){
        time = s;
    }
    public String getName(){
        return name;
    }
    public String getLocation(){
        return location;
    }
    public String getTime(){
        return time;
    }
}

```
## Main
``` java
{
    public static void main(String[] args) {

        Course currentCourse = new Course();
        currentCourse.setCourseNumber("ECE297");
        currentCourse.setCourseTitle("Digital Systems Design");
        OfferedCourse offeredCourse = new OfferedCourse();
        offeredCourse.setCourseNumber("ECE297");
        offeredCourse.setCourseTitle("Embedded Systems Design");
        offeredCourse.setName("Mark Patterson");
        offeredCourse.setLocation("Wilson Hall 231");
        offeredCourse.setTime("WF: 2-2:30 pm");

        currentCourse.printInfo();
        offeredCourse.printInfo();
        System.out.println("    Instructor name: " + offeredCourse.getName());
        System.out.println("    Location: " + offeredCourse.getLocation());
        System.out.println("    Class Time: " + offeredCourse.getTime());
    }
}
```
