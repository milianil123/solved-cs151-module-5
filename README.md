Download Link: https://assignmentchef.com/product/solved-cs151-module-5
<br>
Design a class Numbers that can be used to translate whole dollar* amounts in the range of 0 through 9999 into an English description* of the number.** Algorithm:* 1. Accept input from user. Validate that number is between 0 and 9999* 2. Determine how many digits the number has* 3. Using the number of digits, select the most significant digit and* output it in English* 4. Remove the most significant digit to move place value lower* 5. Continue to determine the most significant digit, display it* in English, and lower the place value until the number is less than* 20*/

#include &lt;iostream&gt;

using namespace std;

class Number{private:int number;

public:Number(int);const static string LESSTHAN20[];const static string TENS[];const static string HUNDRED;const static string THOUSAND;int getNumber();int parseDigits(int);void print();};

Number::Number(int n){number = n;}

const string Number::LESSTHAN20[] = { “zero”, “one”, “two”, “three”, “four”, “five”, “six”, “seven”, “eight”, “nine”, “ten”,“eleven”, “twelve”, “thirteen”, “fourteen”, “fifteen”, “sixteen”, “seventeen”,“eighteen”, “nineteen” };const string Number::TENS[] = { “twenty”, “thrity”, “forty”, “fifty”, “sixty”, “seventy”, “eighty”, “ninety” };const string Number::HUNDRED = “hundred”;const string Number::THOUSAND = “thousand”;

int Number::getNumber(){return number;}

/*** Count the number of digits in the numeral provided*/int Number::parseDigits(int num){return floor(log10(num) + 1);}

void Number::print(){int digits = parseDigits(number);int msd = 0;

// Using the number of digits to deterime where to start dividing// by the highest place valueswitch (digits){case 4:msd = number / 1000; // Determine value of most significant digitcout &lt;&lt; LESSTHAN20[msd];cout &lt;&lt; ” ” &lt;&lt; THOUSAND &lt;&lt; ” “;case 3:number = number % 1000; // as the code falls through,// need to chop off the previous most significant digitmsd = number / 100; // Determine value of most significant digitcout &lt;&lt; LESSTHAN20[msd];cout &lt;&lt; ” ” &lt;&lt; HUNDRED &lt;&lt; ” “;default:number = number % 100; // chop off previous msdif (number &lt; 20){cout &lt;&lt; LESSTHAN20[number] &lt;&lt; endl;} else{msd = number / 10; // Determine value of most significant digitcout &lt;&lt; TENS[msd – 2];cout &lt;&lt; ” ” &lt;&lt; LESSTHAN20[number % 10] &lt;&lt; endl;}}}

int inputNumber();

int main(){Number n(inputNumber());

n.print();

return 0;}

int inputNumber(){int num;bool validInput = false;cout &lt;&lt; “Enter a number between 0 and 9999:
”;cin &gt;&gt; num;

while (!validInput) {if (num &lt; 0 || num &gt; 9999) {cout &lt;&lt; “Invalid input. Re-enter number between 0 and 9999.
”;cin &gt;&gt; num;} else {validInput = true;}}

return num;}