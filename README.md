# nguyenvantuongkhoibaiktra
I. PHẦN LÝ THUYẾT & CÂU HỎI NGẮN
Câu 1: 
Value Types và Reference Types khác nhau chủ yếu ở cách lưu trữ và cách sao chép dữ liệu.
- Value Types: Ví dụ int, double, bool, struct, enum. Biến chứa trực tiếp giá trị. Với biến cục bộ thông thường, giá trị thường được lưu trên Stack.
- Reference Types: Ví dụ class, array, string, object. Biến chứa một tham chiếu đến đối tượng; đối tượng thường được cấp phát trên Heap.
Khi gán Value Type, giá trị được sao chép độc lập:
int a = 10;
int b = a;
b = 20;
// a = 10, b = 20
Với Reference Type, tham chiếu được sao chép nên hai biến có thể cùng trỏ đến một đối tượng:
class Person
{
    public string Name;
}
Person p1 = new Person();
p1.Name = "An";
Person p2 = p1;
p2.Name = "Bình";
// p1.Name cũng là "Bình"
Lưu ý: Không nên hiểu tuyệt đối rằng Value Type luôn nằm trên Stack và Reference Type luôn nằm trên Heap. Vị trí thực tế phụ thuộc vào ngữ cảnh và cách CLR quản lý bộ nhớ. Điểm quan trọng là Value Type chứa giá trị, còn Reference Type chứa tham chiếu đến object.
Câu 2: 
Thuộc tính dùng set có thể được thay đổi sau khi object đã được tạo.
class Student
{
    public string Name { get; set; }
}
Student s = new Student();
s.Name = "An";
s.Name = "Bình"; // Có thể thay đổi
Thuộc tính dùng init chỉ cho phép gán giá trị trong quá trình khởi tạo object. Sau khi khởi tạo xong thì không thể thay đổi.
class Student
{
    public string Name { get; init; }
}
Student s = new Student
{
    Name = "An"
};
// s.Name = "Bình"; // Lỗi
Trường hợp sử dụng thực tế: dùng init cho các đối tượng có dữ liệu cần cố định sau khi tạo, chẳng hạn thông tin sinh viên, cấu hình ứng dụng hoặc DTO.
Câu 3: 
virtual được khai báo ở lớp cha và cho phép lớp con ghi đè phương thức đó.
override được khai báo ở lớp con để cung cấp cách triển khai mới cho phương thức virtual của lớp cha.
Ví dụ:
class Animal
{
    public virtual void Sound()
    {
        Console.WriteLine("Animal sound");
    }
}
class Dog : Animal
{
    public override void Sound()
    {
        Console.WriteLine("Gâu gâu");
    }
}
Khi sử dụng:
Animal animal = new Dog();
animal.Sound();
Kết quả:
Gâu gâu
Đây là tính Đa hình: biến có kiểu Animal nhưng khi chạy lại gọi phiên bản Sound() của Dog.
Tóm lại:
- virtual: Phương thức ở lớp cha có thể được lớp con ghi đè.
- override: Lớp con ghi đè phương thức của lớp cha.
Câu 4: 
Thành phần static thuộc về Class chứ không thuộc về từng Object Instance. Vì vậy, một thành phần static chỉ có một bản dùng chung cho toàn bộ class.
Ví dụ:
class Student
{
    public static int Count = 0;
}
Count phải được truy cập thông qua tên lớp:
Student.Count++;
Không truy cập thông qua object:
Student s = new Student();
s.Count++; // Không hợp lệ
Ngược lại, thành phần không static thuộc về từng object. Ví dụ, mỗi Student có thể có một Name khác nhau.
Kết luận:
- static member thuộc về Class.
- instance member thuộc về Object.
- Vì static không thuộc về một object cụ thể nên phải truy cập bằng tên lớp, không phải thông qua object được tạo bằng new.
