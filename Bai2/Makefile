CC = gcc
CFLAGS = -Wall -pthread
TARGET = canteen
TARGET2 = canteen_2

all: $(TARGET) $(TARGET2)  # Biên dịch cả hai chương trình

$(TARGET): canteen.o
	$(CC) $(CFLAGS) -o $(TARGET) canteen.o

$(TARGET2): canteen_2.o
	$(CC) $(CFLAGS) -o $(TARGET2) canteen_2.o

canteen.o: canteen.c
	$(CC) $(CFLAGS) -c canteen.c

canteen_2.o: canteen_2.c
	$(CC) $(CFLAGS) -c canteen_2.c

clean:
	rm -f $(TARGET) $(TARGET2) *.o

run: $(TARGET)
	./$(TARGET) 5  # Chạy canteen với tham số mặc định (5)

run2: $(TARGET2)
	./$(TARGET2) 5  # Chạy canteen_2 với tham số mặc định (5)
