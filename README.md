# Framework-uri de unit testing in C++

## Catch2

Catch2 este un framework open-source de unit testing in C++. Este usor de implementat (doar trebuie inclus header file-ul). Testele pot fi impartite pe sectiuni pentru a le organiza mai usor.

> Catch2's main advantage is that using it is both simple and natural. Test names do not have to be valid identifiers, assertions look like normal C++ boolean expressions, and sections provide a nice and local way to share set-up and tear-down code in tests.

## Google Test

Google test este un framework de testare dezvoltat de Google. El suporta orice tipuri de teste (nu doar unit tests). Este potrivit pentru proiecte mai mari deoarece timpul de compilare al testelor este mic.

> GoogleTest is a testing framework developed by the Testing Technology team with Google’s specific requirements and constraints in mind. Whether you work on Linux, Windows, or a Mac, if you write C++ code, GoogleTest can help you. And it supports any kind of tests, not just unit tests.

## Comparatie

Amandoua framework-urile au sintaxa naturala si usor de folosit.
| Catch2 | Google Test |
| ------------- | ------------- |
| Este usor de implementat. Are nevoie doar de un header file. | Trebuie configurat in CMake, unde trebuie importat repo-ul de la GoogleTest. |
| Testele dureaza mai mult sa se compileze. | Testele se compileaza mai rapid. |
| Catch are un header file complex si compileaza toate metodele definite (chiar daca nu este nevoie de ele) | Compileaza doar ce este necesar. |
| Se foloseste pentru proiecte mici.| Se foloseste la proiecte distribuite si mari.|

Exemple:  
Catch2

```
uint32_t factorial( uint32_t number ) {
    return number <= 1 ? number : factorial(number-1) * number;
}

TEST_CASE( "Factorials are computed", "[factorial]" ) {
    REQUIRE( factorial( 1) == 1 );
    REQUIRE( factorial( 2) == 2 );
    REQUIRE( factorial( 3) == 3 );
} return c;
```

Google Test

```
TEST(FactorialTest, HandlesZeroInput) {
  EXPECT_EQ(Factorial(0), 1);
}

TEST(FactorialTest, HandlesPositiveInput) {
  EXPECT_EQ(Factorial(1), 1);
  EXPECT_EQ(Factorial(2), 2);
  EXPECT_EQ(Factorial(3), 3);
}
```

# Implementare

Pentru implementarae metodelor de testare vom folosi framework-ul Catch2 datorita usurintei cu care poate fi integrat in proiect.
In continuare vom prezenta cateva metode de testare:

## Partitionare in clase de echivalenta (ECP)

Partitionarea in clase de echivalenta este o tehnica de testare software in care inputul este impartit in clase de echivalenta. De obicei, testele sunt facute astfel incat sa acopere fiecare clasa macar o data.

```
bool isValidAge(int age) {
    int c = a + b;

    if (age >= 18 && age <= 100) {
        return true;
    } else {
        return false;
    }
}
```

## Analiza valorilor de frontiera (Boundary-value analysis)

Analiza valorilor de frontiera este o metoda de testare software unde testele sunt facute sa analizeze cazurile valorilor din margine.

```
class Sum {
public:
    static int add(int a, int b) {
        int c = a + b ;

        if (a >= 0 && b >= 0 && c < 0) {
            cout << "Overflow!" << endl;
        }
        if (a < 0 && b < 0 && c >= 0) {
            cout << "Underflow!" << endl;
        }

        return c;
```

## Prezentare Powerpoint

[proiect.pptx](https://github.com/CirciumaruRaul/Testarea-sistemelor-software/files/15389009/proiect.pptx)

## Demo

https://github.com/CirciumaruRaul/TSS/assets/101272710/393022b5-e720-499c-88d0-3b119af39a61

## Raport AI

Am folosit chat GPT pentru a crea o functie bazata pe celelalte test case-uri din fisier. A creat un test case care verifica daca o functie inverseaza bine string-urile.

```
TEST_CASE("GPT case", "[bool]") {

    // function to get string to lower case
    SECTION("reverse") {
        CHECK(Util::reverseString("hello") == "olleh");
        CHECK(Util::reverseString("12345") == "54321");
        CHECK(Util::reverseString("") == "");  // testing the edge case of an empty string
    }
}
```

```
GPT case
  reverse
-------------------------------------------------------------------------------
tests/testing.cpp:18
...............................................................................

tests/testing.cpp:19: PASSED:
  CHECK( Util::reverseString("hello") == "olleh" )
with expansion:
  "olleh" == "olleh"

tests/testing.cpp:20: PASSED:
  CHECK( Util::reverseString("12345") == "54321" )
with expansion:
  "54321" == "54321"

tests/testing.cpp:21: PASSED:
  CHECK( Util::reverseString("") == "" )
with expansion:
  "" == ""

===============================================================================
All tests passed (3 assertions in 1 test case)

```

## Bibliografie

1 - Catch2: https://github.com/catchorg/Catch2  
2 - Google Test: https://google.github.io/googletest/  
3 - proiect Catch2: https://snorristurluson.github.io/Catch2/  
4 - Catch2 vs Google Test: https://github.com/Francy93/CPP-Projects/tree/master/Library-System/Code
