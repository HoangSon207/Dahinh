#include <iostream>
#include <vector>
#include <memory>

class Animal {
public:

    virtual void speak() const {
        std::cout << "Animal makes a sound\n";
    }

    virtual ~Animal() = default;
};

class Dog : public Animal {
public:
    void speak() const override {
        std::cout << "Dog: Gau gau!\n";
    }
};

class Cat : public Animal {
public:
    void speak() const override {
        std::cout << "Cat: Meo meo!\n";
    }
};

int main() {
    std::vector<std::unique_ptr<Animal>> animals;
    animals.push_back(std::make_unique<Dog>());
    animals.push_back(std::make_unique<Cat>());

    for (const auto& animal : animals) {
        animal->speak();
    }

    return 0;
}
