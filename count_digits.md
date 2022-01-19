# Count number of digits
```
public class MyClass {
    public static void main(String args[]) {
      int n=2225;
      System.out.println(digits(n));
    }
    static int digits(int num) {
        return (int)(Math.log10(num))+1;
    }
}
```
