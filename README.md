# Lab3cpp
Laborator 3 Simboteanu Alexandru DJ2202
EX 1
//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
#include <iostream>

template <typename T>
T min3(const T& a, const T& b, const T& c) {
    return std::min(std::min(a, b), c);
}

int main() {


    std::cout << "Introdu 3 variabile\n";
    std::cout << "Variabila 1: ";
    double var1;
    std::cin >> var1;

    std::cout << "Variabila 2: ";
    double var2;
    std::cin >> var2;

    std::cout << "Variabila 3: ";
    double var3;
    std::cin >> var3;


    std::cout << "Cel mai mic numar este  " << min3(var1, var2, var3) << std::endl;

    return 0;
}
EX2
//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
#include <iostream>

template <typename T>
class Complex {
public:
    T real;
    T imag;

    Complex() : real(0), imag(0) {}

    Complex(T r, T i) : real(r), imag(i) {}

    void setFromInput() {
        std::cout << "Introdu partea reala: ";
        std::cin >> real;

        std::cout << "Introdu partea imaginara: ";
        std::cin >> imag;
    }

    void display() {
        std::cout << real << " + " << imag << "i" << std::endl;
    }
};

int main() {

    Complex<float> complexNum;
    complexNum.setFromInput();  
    complexNum.display();      

    return 0;
}
EX3
//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
#include <iostream>
#include <algorithm>
#include <initializer_list>

template <typename T, int Size>
class Array {
private:
    T data[Size]{};

public:
    // Constructor cu std::initializer_list
    Array(std::initializer_list<T> values) {
        std::copy(values.begin(), values.end(), data);
    }

    // Constructor fara argumente
    Array() = default;

    // Valorile de la tastatura
    void setValues() {
        for (int i = 0; i < Size; ++i) {
            std::cout << "Introdu o valoare : ";
            std::cin >> data[i];
        }
    }

    // Constructor de copiere
    Array(const Array& other) {
        std::copy(other.data, other.data + Size, data);
    }

    // Operatorul de atribuire
    Array& operator=(const Array& other) {
        if (this != &other) {
            std::copy(other.data, other.data + Size, data);
        }
        return *this;
    }

    // Destructor
    ~Array() = default;

 

    // Functia membru size
    int size() const {
        return Size;
    }

    // Functia membru fill
    void fill(const T& value) {
        std::fill(data, data + Size, value);
    }

    // Operatorul de inserare in flux
    friend std::ostream& operator<<(std::ostream& os, const Array& arr) {
        os << "[ ";
        for (int i = 0; i < Size; ++i) {
            os << arr.data[i];
            if (i < Size - 1) {
                os << ", ";
            }
        }
        os << " ]";
        os.flush(); 
        return os;
    }
};

int main() {
    Array<int, 5> intArray;
    intArray.setValues();

    std::cout << "Array initial: " << intArray << std::endl;

    intArray.fill(8);
    std::cout << "Array dupa fill: " << intArray << std::endl;

    Array<int, 5> copiedArray = intArray;
    std::cout << "Array copiat: " << copiedArray << std::endl;

    return 0;
}
