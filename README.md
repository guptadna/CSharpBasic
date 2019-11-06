.NET C#

**************** ShortCuts ***************

https://docs.microsoft.com/en-us/visualstudio/ide/navigating-code?view=vs-2019

Atl + Drag                    --> Vertical selection column
Ctrl + K + D                  --> format in current format setting
Ctrl + -  ( OR ctrl + shift + Del )  --> t go back to previous method
Ctrl + Shift + R              --> Refactor
Ctrl + F5  —   To Execute
cw (First Capital Letters )   --> Tab (sometime press tab twice)   — AutoComplete  ( cw is for Console.Writeline(“”);
Ctrl + X.                     --> to delete a line
Atl + W, R                    --> to reset window layout
Ctrl M + M                    --> collepse uncolleope
Ctrl R + R                    --> refactor rename
F12                           --> display symbol definition
Ctrl + F12                    --> Display symbol declaration
Shift + F12                   --> to find all references
Ctrl + M + O                  --> to fold all methods
Ctrl + M + L                  --> to unfold all methods
Ctrl + T                      --> to open a file


**************** Tools - Addins  ***************

to install new addins
Tools - "Extensions and Updates"

**************** Execute Test ***************

dotnet test LiftOff.Tests.EDIS --filter testcategory=propertyedis

**************** Code ***************

System.Diagnostics.Debug.WriteLine("aaa");
System.Diagnostics.Debug.WriteLine(JsonConvert.SerializeObject(s));

**************** Code - Send REST api with OAuth ***************

            var client = new WebClient();
            String userName = OAuthUsername;
            String passWord = OAuthPassword;
            string credentials = Convert.ToBase64String(Encoding.ASCII.GetBytes(userName + ":" + passWord));
            client.Headers[HttpRequestHeader.Authorization] = "Basic " + credentials;
            var response = client.UploadString(OAuthHost, "");

**************** Code - Send REST api with Bearer ***************

            var client = new WebClient();
            client.Headers[HttpRequestHeader.Authorization] = "Bearer " + Get_TOKEN();
            var response = client.DownloadString(URL_GetPropertyLod(TD1_propertyGuid));

**************** Code - Deserialize Object ***************
            Property ResposneObject = JsonConvert.DeserializeObject<Property>(response);

**************** Read JToken ***************

            var jT = enrichmentAction.AdditionalInformation;
            var b1 = jT.SelectToken("borrower1");

**************** Code - Dictionary ***************
marks.Keys.ElementAt(1)

**************** Date and Time ***************

        static void Main(string[] args)
        {
            // 1 . get current time in epoch and convert into dateTime object
            // 2. get time in epoch and convert into date time object
            // 3. get Timespan of date 1 and date 2.

            var epoch = (DateTime.UtcNow - new DateTime(1970, 1, 1, 0, 0, 0, DateTimeKind.Utc)).TotalSeconds;
            DateTime starTime = UnixTimeStampToDateTime(epoch);
            Console.WriteLine("starTime : " + starTime);


            Thread.Sleep(10000);


            DateTime endTime = DateTime.UtcNow;
            Console.WriteLine("endTime : " + endTime);

            TimeSpan elapsed = endTime.Subtract(starTime);
            Console.WriteLine("elapsed : " + elapsed.TotalMilliseconds);

            Console.ReadLine();
        }

        public static DateTime UnixTimeStampToDateTime(double unixTimeStamp)
        {
            // Unix timestamp is seconds past epoch
            System.DateTime dtDateTime = new DateTime(1970, 1, 1, 0, 0, 0, 0, System.DateTimeKind.Utc);
            dtDateTime = dtDateTime.AddSeconds(unixTimeStamp).ToUniversalTime();
            return dtDateTime;
        }

**************** Expression ***************

Name :
Expression :    ?.
Example :       LoanOriginationId = LoanOrigination?.OriginationInfo?.LoanOriginationId

nameof(object) --> Return literal string class name


Name : Null-Collation
Expression : ??
Example:

string name = null;
string myname = name ?? "Laxmi";

Result  : Laxmi
URL : https://dzone.com/articles/nullable-types-and-null-coalescing-operator-in-c


***************** Dot net test ************

working
dotnet test WM.Tests --filter FullyQualifiedName=WM.Tests.IntegrationTests.WorkItemScoringTests.WorkitemScoring_AllValidFields
dotnet test WM.Tests --filter DisplayName=WM.Tests.IntegrationTests.WorkItemScoringTests.WorkitemScoring_AllValidFields
dotnet test WM.Tests --filter DisplayName~ProcessEngineAPITests.PE_GetProcessById_Valid

ProcessEngineAPITests.PE_GetProcessById_Valid

cd C:\Users\agupta1\gitProjectWin\WorkManagerTests\WM.Tests\
dotnet test C:\Users\agupta1\gitProjectWin\WorkManagerTests\WM.Tests --filter FullyQualifiedName=ProcessEngineAPITests.PE_EndtoEnd()
dotnet test --filter FullyQualifiedName=ProcessEngineAPITests.PE_EndtoEnd()
dotnet test WM.Tests --filter testcategory=workitemscoring
dotnet test WM.Tests --filter Name=PE_StartAProcess
TaskToRoleTests.TaskToRole_Negative_InvalidJSON_TEXT()
WorkItemScoringTests.WorkitemScoring_AllValidFields()
ProcessEngineAPITests.PE_EndtoEnd()

WM.Tests.IntegrationTests.WorkItemScoringTests.WorkitemScoring_AllValidFields
dotnet test WM.Tests --filter FullyQualifiedName=WM.Tests.IntegrationTests.WorkItemScoringTests.WorkitemScoring_AllValidFields
DisplayName


dotnet test C:/Users/agupta1/gitProjectWin/myProjects/GUI/XUnitTestProject --filter DisplayName~UnitTestA.Test1
dotnet test C:\Users\agupta1\gitProjectWin\myProjects\GUI/XUnitTestProject --filter DisplayName~UnitTestA.Test1

Passed: 1. Failed

## Regular Expression
```
            string workDefIdPattern = @"[0-9]{4}";
            Match result = Regex.Match(responseObject.WorkDefId.ToString(), workDefIdPattern);
            Assert.True(result.Success, "WorkDefId");

            Assert.True(Regex.Match(responseObject.Id.ToString(), @"[0-9]{6}").Success, "WorkDefId");
 ```
 
 ## CSharp
 
 CSharp C# basic
=====


**Variables type**
non-static - instance variable
static - class variable, static constructor can be used to initialize the static variable
const - should be initialized at the time of declaration
readonly - initialize the variable one time, mostly in the constructor, once initialized can not be modified,

**Variable vs Property**
Variable hold the value
Property provide access to variable

Variable Example
```
private int _marks;
public string _name;
```
Property Example
```
public string name{ get; set};

public string name{ get;};

public string name{ set;};

public int marks
        {
            get { return _marks; }
            set { _marks = value; }
        }

public string Name
        {
            get
            {
                return name.ToUpper();
            }
            set
            {
                if (value == "Suresh")
                    name = value;
            }
        }}
```

**Assess Modifier**
private
protected - accessible to child classes within project and outside the project
protected internal - accessible to child classes within project and but not outside the project
internal - it is like default in java, scope within a project
public

**Constructor**
Regular - whenever an instance is created
Static - execute at once at class execution

Calling base class parameterized constructor ( or passing values to base class constructor), We need to use "base" keyword.
Example :
```
ChildClass(value1, value2):base(value1)
```

**Array vs Collection**
Array - fixed length, can't insert/delete in the middle, type safe
ArrayList - variable length, can insert/delete in the middle, not typesafe
HashTable --Key/Value pair but not in a sequential fashion, not typesafe

**Non Generic     |      Generic**
Arraylist         --> List<T>
HashTable         --> Dictionary<Tkey,Tvalue>
SortedList        --> SortedList<Tkey,Tvalue>
Stack            --> Statck<T>
Queue             --> Queue<T>
                  --> HashSet<T>

```
            Dictionary<int, string> NameList = new Dictionary<int, string>();
            NameList.Add(1001, "tom");
            NameList.Add(1002, "dick");
            NameList.Add(1003, "harry");

            foreach (var i in NameList)
            {
                Console.WriteLine($"{i.Key} : {i.Value}");
            }

            for (int i = 0; i < NameList.Count; i++)
            {
                Console.WriteLine($"{NameList.ElementAt(i).Key} : {NameList.ElementAt(i).Value}");
            }
```

**Overriding vs Method hiding**

overriding can be done two ways:
A) Method Overriding approach
to override a a parent class method by a child class method,
1) In parent class, method should declared with *virtual* keyword that shows this method is overridable
2) In child class, method should use keyword "override".
Example :
In parent class
```
public virtual void Test();
```
In child class
```
public override void Test();
```

B) Method hiding approach
Method not declared as virtual in parent class still can be override by child class.
Example
in child class, both way it can work.
```
public new void Test(); or
public void Test();
```

**Inheritance**
1) By creating an instance of parent class under child class, parent class methods can be accessed.
2) By using base keyword also, we can call parent's class methods using "base" and "this" keyword.
3) parent class reference even if instantiated using child class, can not access purely child class method but can call overridden members of child class, because overridden members are not considered as pure child class members, but members which are re-implemented by using the approach of hiding are considered as pure child class members and are not accessible to parent's references.

**LINQ**
```
            Dictionary<int, string> NameList = new Dictionary<int, string>()
            {
                {1001, "tommy"},
                {1002, "jimmy"},
                {1003, "harry"}
            };
            var myLinqQuery = from name in NameList
                              where name.Value.Contains("m")
                              select name;

            foreach (var name in myLinqQuery)
                Console.WriteLine(name);
```

**How to access methods**
1) By calling class instance ( for non static methods)
2) by Calling Class name ( for static method)
3) by Delegate method

**How to access class variables**
 indexes is another approach to access class Variables

Delegates
Anonymous method
Lambda

**Multi-Thread**
```
Thread t = new Thread(sumMethod);
t.start();
t.join() //to make sure main thread waits
t.abort() // to abort the thread

```
**Multi-Thread - lock a method**
in the multi thread environment, it may happen a specific method can be invoked by multiple threads and can disturb the value of variables and etc. Csharp provides the lock mechanism to lock the block so one thread can use at a time.
```
        public void CounterWithLock()
        {
            lock (this)
            {
                for (int i = 0; i <= 100; i++)
                {
                    if (i == 50)
                    {
                        Console.WriteLine("i : " + i + " : thread is sleeping");
                        Thread.Sleep(5000);
                    }

                    Console.WriteLine("i : " + i);
                }
            }
        }
```


**Delegate**
When to use: When we want to execute series of methods with the same inputs and not expecting return type.
1)It is a type safe function pointer.
2) Delegate holds the reference of a method and then calls the method for execution. It should have same parameter and return type as method it is referencing to.
3) to call delegate we need to perform 3 steps

a) define
```
public delegate int AddDelegate(int a, int b);
```
b) create delegate instances
```
AddDelegate addDelegate = new AddDelegate(p.Add);
or
AddDelegate addDelegate = p.Add;
or
AddDelegate addDelegate = delegate p.Add;
```
c)  Call/Execution
```
addDelegate(10, 5)
```
Program Example
```
namespace DelegateExample
{
    public delegate int AddDelegate(int a, int b);
    class Program
    {
        static void Main(string[] args)
        {
            Program p = new Program();
            Console.WriteLine("Hello World!");
            AddDelegate addDelegate = new AddDelegate(p.Add);
            Console.WriteLine(addDelegate(10, 5));
            Console.ReadLine();
        }

        public int Add(int a, int b)
        {
            return a + b;
        }
    }
}

```

**multiple Delegate**
multiple method can be added to delegate but previous methods results will be overridden by last method result.
```
Rec del = new Rec(p.GetArea);
del = del + p.GetPrimeter;
```
**Extension Method**

 
