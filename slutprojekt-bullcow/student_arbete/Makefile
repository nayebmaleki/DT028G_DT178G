CXX=g++
CXXFLAGS=-std=c++17 -Wall -Wextra -Wpedantic
TARGET=bullcow
SOURCES=src/main.cpp src/bullcow.cpp
.PHONY: all clean
all: $(TARGET)
$(TARGET): $(SOURCES)
	$(CXX) $(CXXFLAGS) $(SOURCES) -o $(TARGET)
clean:
	rm -f $(TARGET) *.o
