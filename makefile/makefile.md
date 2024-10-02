# Makefile
---
![alt text](image.png)
![alt text](image-1.png)
![alt text](image-2.png)
![alt text](image-3.png)
![alt text](image-4.png)
![alt text](image-5.png)
![alt text](image-6.png)
![alt text](image-7.png)
![alt text](image-8.png)
![alt text](image-9.png)
![alt text](image-10.png)
![alt text](image-11.png)
![alt text](image-12.png)
![alt text](image-13.png)
![alt text](image-14.png)
![alt text](image-15.png)
![alt text](image-16.png)
![alt text](image-17.png)
![alt text](image-18.png)
![alt text](image-19.png)
![alt text](image-20.png)
![alt text](image-21.png)
![alt text](image-22.png)
![alt text](image-23.png)
![alt text](image-24.png)
Dù viết là 1 nhưng 1 ở đây là ký tự chứ không phải số nguyên
![alt text](image-25.png)
Lệnh để xem predefined variable values
![alt text](image-26.png)
![alt text](image-27.png)
![alt text](image-28.png)
![alt text](image-29.png)
![alt text](image-30.png)
![alt text](image-31.png)
![alt text](image-32.png)
![alt text](image-33.png)
![alt text](image-34.png)
![alt text](image-35.png)
![alt text](image-36.png)
![alt text](image-37.png)
![alt text](image-38.png)
![alt text](image-39.png)
wildcard và patsubst đều là hàm trong makefile
patsubst là viết tắt của path substitution
![alt text](image-40.png)
![alt text](image-41.png)
Sẽ ra sao khi các file source nằm trong thư mục riêng và file header nằm ở một thư mục riêng?
![alt text](image-42.png)
makefile sẽ nằm ở ngoài cùng nhé
![alt text](image-43.png)
Sử dụng slash
![alt text](image-44.png)
![alt text](image-45.png)
-I để compiler biết nhìn vào đâu để tìm các file include
![alt text](image-46.png)
![alt text](image-47.png)
Chưa có folder build thì tạo mới
![alt text](image-48.png)
Thêm các điều kiện về warning
![alt text](image-49.png)
.PHONY để làm gì
![alt text](image-50.png)
![alt text](image-51.png)
![alt text](image-52.png)
![alt text](image-53.png)
![alt text](image-54.png)
![alt text](image-55.png)
![alt text](image-56.png)
![alt text](image-57.png)
![alt text](image-58.png)
![alt text](image-59.png)
![alt text](image-60.png)
![alt text](image-61.png)
![alt text](image-62.png)
![alt text](image-63.png)
![alt text](image-64.png)

```makefile
# Đường dẫn tới các thư mục
SRC_DIR = src
INC_DIR = include
BUILD_DIR = build

# Danh sách tất cả các file nguồn (.c) trong các thư mục
SRCS = $(shell find $(SRC_DIR) -name '*.c')

# Danh sách tất cả các file tiêu đề (.h) trong các thư mục
HEADERS = $(shell find $(SRC_DIR) -name '*.h') $(shell find $(INC_DIR) -name '*.h')

# Tạo tên file thực thi từ tên file đầu vào
TARGET = $(BUILD_DIR)/app

# Biến cho trình biên dịch và các tùy chọn
CC = gcc
CFLAGS = -I$(INC_DIR) -I$(SRC_DIR) -Wall -g

# Danh sách các file đối tượng (.o)
OBJS = $(SRCS:$(SRC_DIR)/%.c=$(BUILD_DIR)/%.o)

# Mục tiêu mặc định
all: $(TARGET)

# Quy tắc để tạo file thực thi
$(TARGET): $(OBJS)
	$(CC) -o $@ $^

# Quy tắc để tạo file đối tượng từ file nguồn
$(BUILD_DIR)/%.o: $(SRC_DIR)/%.c
	$(CC) $(CFLAGS) -c $< -o $@

# Mục tiêu để xóa các file biên dịch
clean:
	rm -f $(BUILD_DIR)/*.o $(TARGET)

.PHONY: all clean
```
![alt text](image-65.png)
![alt text](image-66.png)