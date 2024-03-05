# 제어문

Ex) 사용자의 인증이 필요한 웹사이트 (로그인 기능이 있는 웹사이트)

→ 사용자가 올바른 비밀번호를 입력했을 때만 그 사용자의 개인 정보를 보여줘야함

→ 로그인이 실패했을 때는 누구인지 물어봐야함

즉, 사용자가 올바른 비밀번호를 입력했는지 안했는지에 따라서 프로그램의 동작이 달라져야 함

>> 이런 작업을 위해서 필요한 것이 조건에 따라서 실행되는 순서를 제어하는 **조건문(Conditional statement)**

→ 우리가 처리해야 될 데이터가 1억 건이라면? 

>> 엄청나게 많은 데이터를 반복적으로 처리할 때 사용하는 것을 **반복문 (Loop statement)**

시간의 순서에 따라서 실행되는 프로그램이 물이 흐르도록 하는 중력 이라고 한다면,

조건문과 반복문은 이 물의 흐름을 바꾸는 댐의 역할을 한다.

---

## 조건문(Conditional statement)

주어진 조건식의 결과에 따라 별도의 명령을 수행하도록 제어하는 명령문

- if 조건문

if 조건문의 소괄호 안에는 true / false 값이 들어가야한다.

만약 조건이 true라면 중괄호 안의 코드가 실행되고, false면 실행이 되지 않는다.

```java
if (조건식) { //조건식은 boolean 타입만 가능
    실행문; //조건식이 true일 경우 수행
}

if(true) { // 괄호 안의 값이 true이면 중괄호 안의 코드가 실행된다. false면 실행되지 않는다.
    System.out.println(1);
}

```

만약 조건이 true이면 어떤 코드를 실행하고 false면 다른 코드를 실행하고 싶다면?

→ else 사용 (조건이 true가 아닌 경우)

```java
if(true) {
    System.out.println(1);
} else {
    System.out.println(2);
}
```

if문 안에 또 다시 if문이 들어갈 수 있다. 이를 ‘중첩된 if문’ 이라고 부른다.

```java
if(true) {
        System.out.println(1);
} else {
        if (true){
                System.out.println(2);
        } else {
                System.out.println(3);
        }
}
```

하지만  위와 같은 중첩된 if문을 사용하면 코드가 한눈에 들어오지 않는다는 단점이 있다.

이럴 때는 else if를 사용하면 보다 깔끔하게 조건을 설정할 수 있다.

먼저 if 조건을 살피고, 아니라면 그 다음 else if의 조건을 살피고, 그것도 아니라면 else로 넘어가서 코드를 실행하게 된다.

```java
if(false) {
        System.out.println(2);
} else if(true) {
      System.out.println(1);
} else {
        System.out.println(3);
}
```

- switch문

조건식의 결과가 정수 또는 문자열 값이고 그 값에 따라 수행되는 경우가 각각 다른 경우에는 switch-case문으로 구성하는 것이 코드로 깔끔하고 가독성이 좋다.

break 키워드를 포함하기도 한다. →  switch문의 수행을 멈추고 빠져나가도록 만든다.

```java
switch(조건) {
    case 값1 : 
        수행문1; 
            break;
    case 값2 : 
        수행문2;
    case 값n :
        수행문3;
    default : // 조건식의 값이 어떤 값과도 일치하지 않을 때
        수행문4; //(생략 가능)
}
```

---

## 조건문 응용

논리연산자를 활용하여 조건문을 더 간단하게 표현할 수 있다.

```java
      String id = "ssoco";
        String inputId = args[0];
        
        String pass = "1111";
        String inputPass = args[1];
        
//        if(inputId.equals(id)) {
//            if(inputPass.equals(pass)) {
//                System.out.println("Master!");
//            } else {
//                System.out.println("Wrong password!");
//            }
//        } else {
//            System.out.println("Who are you?");
//        }
        
        if(inputId.equals(id) && inputPass.equals(pass)) {  //아이디와 비밀번호를 모두 확인
            System.out.println("Master!");
        } else {
            System.out.println("Who are you?");
        }
        
```

논리연산자 &&를 이용해 위 조건문을 좀 더 간단하게 표현하였다.

조건 두개를 &&로 엮어서 두 조건이 모두 만족해야만 "Master!"를 출력되고, 아니라면 "Who are you?"가 출력된다.

## == vs Equals

== 연산자는 주소값을 비교하고, equals 메소드는 값 자체를 비교한다.

- boolean, int, double, short, long, float, char 등의 원시적인 데이터형은 ==를 사용해도 무방
    - 같은 데이터가 다른 주소값을 가지지 않기 때문
- 하지만 String, Array, Date, File 등의 비원시형태의 데이터형은 ==를 사용하면 올바르게 비교가 되지 않을 수 있다.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/bb19166d-a0fa-441d-9390-7b493cb2b1d7/3f81a0c6-7c7e-4314-ae64-10477bd5b105/Untitled.png)

> 실제로 이렇게 사용할 일은 거의 없겠지만, new String("java")를 두 번 반복해서 o1과 o2에 값을 넣어주게 되면, 각 인스턴스는 다른 주소값에 데이터를 가지게 된다.
> 

이 때 두 문자열을 비교하면 주소값이 다르기 때문에 ==로 비교하게 되면 false가 나오는 것이다.

- 자바에서는 문자열에 한해서 편의를 위해서 일반적인 경우에 같은 메모리를 가리키게 한다. 하지만 어디까지나 예외사항이기 때문에, 혹시 모를 상황에 대비해서 equals를 사용하는 것이 조금 더 적합한 방법이다.

---

## 반복문(Loop statement)

- while문

while문은 if문과 유사한 형태이기 때문에 훨씬 이해하기 쉽다.

if문과 동일하게 소괄호 안의 조건을 만족하면 중괄호 안의 코드가 돌아간다.

대신 if문과는 다르게 중괄호 안의 코드가 끝나면 다시 while문의 조건을 확인하고 조건을 만족하면 (true면) 중괄호 안의 코드가 다시 돌아간다.

```java
int i = 0 
while(i < 3) {
        System.out.println(2);
        System.out.println(3);
        i++;
}
```

만약 계속 true라면 무한으로 돌아간다.

while문을 빠져나갈 수 있도록 조치를 취해야 하는데, 위 코드에서 i라는 변수를 이용해서 while문이 한 번 돌때마다 i가 1씩 증가해서 i가 3까지 커지면 더이상 조건을 만족하지 못해서 while문 밖으로 빠져나오게 된다.

- do-while문

중괄호 안의 문장을 반드시 한 번 이상 수행해야 할 때는 while문 대신 do-while문을 사용한다.

```java
초기식; //필수 문법은 아니지만 일반적으로 사용
do {
    실행문; //실행 후 비교. 조건문이 false더라도 최소 1회 실행됨
    증감식; //필수 문법은 아니지만 일반적으로 사용
} while (조건식); //문법 구조상 중괄호가 없으므로 세미콜론(;)으로 끝남
```

- for문

몇 번 반복할 지 이미 알고 있는 상태라면 while문 대신 for문이 더 효과적이다.

기본 형태는 

> for (초기값; 조건문; 증감식){}
> 

초기값은 단 한 번만 작동하고 매번 for문이 돌때마다 증감식이 작동하고, 조건을 확인해서 조건에 맞지 않으면 for문이 끝나게 된다.

```java
for(int j=0; j<3; j++){
        System.out.println(2);
        System.out.println(3);
}
```

for문을 사용하면 반복에 필요한 요소들이 한 곳에 모여있기 때문에 훨씬 이해하기 쉽고 반복에 필요한 요소가 의도치 않게 변화할 위험도 낮아진다.

---

## 제어 키워드

continue 과 break는 일반적인 루프의 흐름을 사용자가 직접 제어할 수 있도록 도와준다.

- break 제어 키워드
    
    루프 내에서 사용하여 해당 반복문을 완전히 종료시킨 뒤, 반복문 바로 다음에 위치한 명령문을 실행하는 제어 키워드이다.
    
    - 루프 내에서 조건식의 판단 결과와 상관없이 반복문을 완전히 빠져나가고 싶을 때 사용한다.
    
    ```java
    // 0부터 시작해 숫자를 1씩 늘리면서 합을 계산할 때 합이 100보다 크기 전까지만 수행
    int sum = 0;
    int num = 0;
    
    for(num = 0; ;num++){ //sum < 100 조건식을 생략하는 대신 break문을 사용합니다. 
        sum += num;
        if (sum >= 100) // sum이 100보다 크거나 같을 때(종료조건)
            break;        // 반복문 중단
    } 
    ```
    
- continue 제어 키워드
    
    루프 내에서 사용하여 해당 루프의 나머지 부분을 건너뛰고, 바로 다음 조건식의 판단으로 넘어가게 해주는 제어 키워드이다.
    
    - 반복문 안에서 continue 문을 만나면 이후의 문장을 수행하지 않고 for문의 처음으로 돌아가 증감식을 수행한다.
    
    ```java
    // 1부터 100까지 수 중에서 3의 배수만 출력하는 코드
    int num;
    
    for (num = 1; num <= 100; num++){
        if(num % 3 != 0)
            continue;
        System.out.println(num);
    }
    ```
    

---

# 배열(Array)

배열(array)은 동일한 자료형을 묶어 저장하는 참조 자료형으로 자료를 순차적으로 관리하는 구조이다.

배열은 index와 element로 구성되어 있다.

어느 위치에 있는 지를 표현하는 것이 index(색인), 그 위치에 있는 데이터가 Element(값)이다.

> 인덱스(index)
> 
> - 자바에서 인덱스는 언제나 0부터 시작하며, 1씩 증가한다.
> - 0을 포함한 양의 정수만을 가질 수 있다.
> - 인덱스는 0부터 시작하기 때문에 `배열의 길이 - 1`이 인덱스 번호가 된다.
> - 배열의 값을 저장할 수 있는 공간에 붙은 방 번호

- 배열의 선언

```
자료형[] 변수명
```

```java
int[] a; //int 자료형만 저장 가능
double[] b; //double 자료형만 저장 가능
String[] c; //String 자료형만 저장 가능
```

형식으로 배열을 만들 수 있다.

위와 같이 선언된 배열은 new 키워드를 사용하여 실제 배열로 생성할 수 있다.

```java
배열이름 = new 타입[배열길이];

//배열의 선언과 생성을 동시에
타입[] 배열이름 = new 타입[배열길이];
int[] grade1 = new int[3];
boolean[] array1 = new boolean[3];
double[] array2 = new double[7];
String[] array3 = new String[9];

int[] studentIDs = {102,103,104}; // int형 요소가 3개인 배열 생성

//배열의 자료형을 먼저 선언하고 초기화하는 경우 >> new int[]를 생략할 수 없다.
int[] studentIDs; //배열 자료형 선언
studentIDs = new int[] {102,103,104}; //new int[]를 생략할 수 없다.
```

---

## 반복문 + 배열

### 배열의 길이 구하기(length)

반복의 횟수를 결정하기 위해서는 배열의 길이를 알아야 한다. 자바에서는 '배열 참조 변수.length'로 배열의 길이를 구할 수 있다.

```java
public class ReadArrayData {
    public static void main(String[] args) {
        int[] array = new int[] {3, 4, 5, 6, 7};
        for(int i = 0; i < array.length; i++) //배열 참조 변수.length
            System.out.print(array[i] + " ");
        System.out.println();
    }
}
```

## 객체 배열 사용하기

먼저 Book 클래스를 만들고 이 클래스로 객체 배열을 만들어야 한다.

```java
package array;

public class Book {

    private String bookName;
    private String author;
    
    public Book(){} // default 생성자
    
    public Book(String bookName, String author){ //책 이름과 저자이름을 매개변수로 받는 생성자
        this.bookName = bookName;
        this.author = author;
    }
    
// 다른 코드에서 이 클래스를 사용할 때 멤버 변수 값을 가져오거나 지정할 수 있도록 
// get(), set() 메서드도 구현
    public String getBookName() {
        return bookName;
    }
    public void setBookName(String bookName) {
        this.bookName = bookName;
    }
    public String getAuthor() {
        return author;
    }
    public void setAuthor(String author) {
        this.author = author;
    }

//책 정보를 출력해주는 메서드
    public void showBookInfo(){
        System.out.println(bookName + "," + author);
    }
}
```

도서관에 책이 5권 있다고 가정한다.

Book 클래스를 사용해 책 5권을 객체 배열로 만든다.

```java
package array;

public class BookArray {

    public static void main(String[] args) {
        Book[] library = new Book[5]; // Book 클래스 형으로 객체 배열 생성
        //각각의 Book 인스턴스 주소 값을 담을 공간 5개를 생성하는 문장이다.
        //Book 주소 값을 담을 공간 5개가 만들어지고 자동으로 각 공간은 null 값으로 초기화됨.
        
        // 배열의 각 요소에 Book 인스턴스를 만들어 직접 저장하였다.
        library[0] = new Book("태백산맥", "조정래");
        library[1] = new Book("데미안", "헤르만 헤세");
        library[2] = new Book("어떻게 살 것인가", "유시민");
        library[3] = new Book("토지", "박경리");
        library[4] = new Book("어린왕자", "생텍쥐페리");
        
        for(int i=0; i<library.length; i++){
            library[i].showBookInfo();
        }
        
        for(int i=0; i<library.length; i++){
            System.out.println(library[i]); //출력내용: 각 배열 요소가 가지고 있는 인스턴스의 주소값
        }
    }
}
```
