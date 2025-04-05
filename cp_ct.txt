#include <iostream>
using namespace std;

// Function to compute GCD using Euclid's algorithm
int gcd(int a, int b) {
    if (b == 0)
        return a;
    return gcd(b, a % b);
}

// Function to compute LCM using GCD
int lcm(int a, int b) {
    return (a / gcd(a, b)) * b;  // To prevent overflow
}

int main() {
    int a, b;
    cout << "Enter two numbers: ";
    cin >> a >> b;

    cout << "GCD of " << a << " and " << b << " is: " << gcd(a, b) << endl;
    cout << "LCM of " << a << " and " << b << " is: " << lcm(a, b) << endl;

    return 0;
}


#include<bits/stdc++.h>
using namespace std;

int main()
{
    int n;
    cin>>n;

    while(n%2==0)
    {
        cout<<2<<" ";
        n/=2;
    }
    for(int i=3; i<=sqrt(n); i+=2)
    {
        while(n%i==0)
        {
            cout<<i<<" ";
            n/=i;
        }

    }
    if(n>1)cout<<n<<endl;


}


#include<bits/stdc++.h>
using namespace std;

int isPrime(int num)
{
    for(int i=2;i<=sqrt(num); i++)
    {
        if(num%i==0)
        {
            return 0;
        }
    }
    return 1;
}

int main()
{
    cout<<"Please Enter a number greater than 1 : ";
    int num;
    cin>>num;

    if(isPrime(num))
    {
        cout<<"The Number is Prime"<<endl;
    }
    else
    {
        cout<<"The Number is not Prime"<<endl;
    }


}



#include<bits/stdc++.h>
using namespace std;

void sieve(int n)
{
    bool isPrime[n+1];

    for(int i=0; i<=n; i++)
    {
        isPrime[i] = true;
    }

    isPrime[0]=isPrime[1]=false;

    for(int p=2; p*p<=n; p++)
    {
        if(isPrime[p])
        {
            for(int i=p*p; i<=n; i+=p)
            {
                isPrime[i]=false;
            }
        }
    }

    for(int i=2; i<=n; i++)
    {
        if(isPrime[i])
        {
            cout<<i<<" ";
        }
    }
}
int main()
{
    int n;
    cin>>n;

    sieve(n);
}


#include <bits/stdc++.h>
using namespace std;

int n = 90000000;
vector<int> v;

void sieve()
{
    bool isPrime[n + 1];

    for (int i = 0; i <= n; i++)
    {
        isPrime[i] = true;
    }

    isPrime[0] = isPrime[1] = false;

    for (int p = 2; p * p <= n; p++) // Fixed loop condition
    {
        if (isPrime[p]) // Fixed condition check
        {
            for (int i = p * p; i <= n; i += p)
            {
                isPrime[i] = false;
            }
        }
    }

    for (int i = 2; i <= n; i++)
    {
        if (isPrime[i])
        {
            v.push_back(i);
        }
    }
}

int main()
{
    sieve();

    int nth;
    cin >> nth;
    cout << v[nth - 1] << endl; // Fixed variable name and indexing

    return 0;
}


#include<iostream>
#include<vector>
#include<math.h>
#include<algorithm>
using namespace std;

int main()
{
    cout<<"Enter a number : ";
    int num;
    cin>>num;

    vector<int>factors;

    for(int fact=1; fact<=sqrt(num); fact++)
    {
        if(num%fact == 0)
        {
            factors.push_back(fact);
            if(fact!=num/fact)
            {
                factors.push_back(num/fact);
            }
        }
    }
    sort(factors.begin(),factors.end());
    cout<<"The divisors of the number are : ";
    for(auto ans:factors)
    {
        cout<<ans<<" ";
    }


    return 0;
}


#include<bits/stdc++.h>
using namespace std;
#define ll long long int

int main()
{
    ll num;
    cin>>num;

    ll temp = num;

    ll power=0 ,total_fact=1 ,sum_fact=1,product_fact=1;
    ll lim=sqrt(num);

    for(ll div=2; div<=lim; ++div)
    {
        power=0;
        while(num%div==0)
        {
            num/=div;
            power++;
        }
        if(power!=0)
        {
            //formula to find total factors of a number
            total_fact *= (power+1);

            //formula to find the sum of all factors of a number
            sum_fact *= (pow(div, power+1)-1)/(div-1);
        }
    }

    if(num>1)
    {
        total_fact *= 2;
        sum_fact *= num+1;
        //product_fact *= num;
    }
    //formula to find product of all factors of a number
    product_fact = pow(temp, total_fact/2);

    //ANSWERS
    cout<<"Total factors of = "<<total_fact<<endl;
    cout<<"Sum of factors of = "<<sum_fact<<endl;
    cout<<"Product of factors of = "<<product_fact<<endl;

}


#include <iostream>
using namespace std;

int phi(int n) {
    int result = n;
    for (int p = 2; p * p <= n; p++) {
        if (n % p == 0) {
            while (n % p == 0)
                n /= p;
            result -= result / p;
        }
    }
    if (n > 1)
        result -= result / n;
    return result;
}

int main() {
    int n;
    cout << "Enter a number: ";
    cin >> n;

    cout << "Euler's Totient Function φ(" << n << ") = " << phi(n) << endl;
    return 0;
}
