nhanh_cua_cuonng
# Dahinh
TÍNH ĐA HÌNH 
1. KHÁI NIỆM
Đa hình nghĩa là “nhiều hình thức”: cùng một tên hàm hoặc toán tử nhưng hành vi khác nhau tùy ngữ cảnh hoặc đối tượng gọi. Ý tưởng cốt lõi là “một giao diện, nhiều cách cài đặt”.
Ví dụ: lớp cha DongVat có hàm keu(); các lớp con Cho, Meo cùng có hàm keu() nhưng mỗi lớp kêu một kiểu.
2. LỢI ÍCH
- Mã nhất quán, dễ đọc: các lớp liên quan dùng chung tên hàm.
- Dễ mở rộng: thêm lớp con mới mà không phải sửa mã đã có.
- Giảm các câu lệnh if/switch kiểm tra kiểu đối tượng.
- 
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
main
