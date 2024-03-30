# Hướng dẫn cài Cocotb và chạy ví dụ
> Hướng dẫn được thực hiện trên Ubuntu  
> Made by **Simulation Team**
## Bước 1: Các yêu cầu cần có trước khi cài Cocotb
### Python 3.6+
> Check version Python
```
python3 --version
```
- Nếu chưa có hoặc version cũ, hãy cài Python:
```
sudo apt-get update
sudo apt-get install python3.6
```
> Check conda
```
conda list
```
- Nếu chưa có conda, truy cập link sau và làm theo các bước hướng dẫn: `https://conda.io/projects/conda/en/latest/user-guide/install/linux.html`
### GNU Make 3+
- Download Source code
```
wget https://ftp.gnu.org/gnu/make/make-4.3.tar.gz
```
- Extract tarball
```
tar xfz make-4.3.tar.gz
```
- Configure the build and install
```
cd make-4.3/
./configure
make
```
### Trình mô phỏng cho Verilog
> Should use both, Icarus is good for a quick (to start) simulation. Verilator is good for exhaustive tests.
##### Icarus Verilog
- Cài packet Iverilog và gtkwave
```
sudo apt install iverilog gtkwave
```

##### Verilator
- Install Prerequisites
```
sudo apt-get install git help2man perl python3 make autoconf g++ flex bison ccache
sudo apt-get install libgoogle-perftools-dev numactl perl-doc
sudo apt-get install libfl2                                                          #(bỏ qua nếu báo lỗi)
sudo apt-get install libfl-dev                                                       #(bỏ qua nếu báo lỗi)
sudo apt-get install zlibc zlib1g zlib1g-dev                                         #(bỏ qua nếu báo lỗi)
```
- Git clone
```
git clone https://github.com/verilator/verilator
```
- Mỗi khi cần build version mới
```
unset VERILATOR_ROOT
cd verilator
git pull                   # Đảm bảo git được cập nhật
git checkout master        # Sử dụng development branch (recent bug fixes)
git checkout stable        # Sử dụng bản ổn định gần nhất
```
- Configure and install
```
autoconf                   # Create ./configure script
./configure                # Configure and create Makefile
make -j `nproc`            # Build Verilator itself (if error, try just 'make')
sudo make install
```

## Bước 2: Cài Cocotb 
- Trong terminal:
```
sudo apt-get install make python3 python3-pip
```
- Cài cocotb
```
pip install cocotb
```
- Check cocotb configure:
```
cocotb-config
```
>Nếu "not found", hãy thử reset và check config lại. Nếu không được thì cần gán location của cocotb vào `PATH` trong environment variable.
## Bước 3: Chạy file
- Git clone 
```
git clone https://github.com/cocotb/cocotb.git
```
- Chạy make tại /cocotb
``` 
cd cocotb
make
```
- Chạy file `setup.py` tại /cocotb
```
sudo ./setup.py build
sudo ./setup.py install
```
>Nếu báo `/usr/bin/env: python: No such file or directory`, thử chạy: `whereis python` rồi tạo liên kết đến đó `sudo ln -s/urs/bin/python/usr/bin/python`.
Sau đó chạy lại file `setup.py` tại cocotb. nếu không được hãy thử `sudo apt install python-is-python3`
- Chuyển đến mục cần chạy test
```
cd examples/adder/tests
```
- Nếu phiên bản conda >= 4.4, cần phải deactive conda environment sau khi install (chỉ cần làm 1 lần sau khi cài conda)
```
conda deactive
```
- Chọn simulator và chạy make
```
make SIM=icarus
```
> nếu dùng **verilator**, hãy thay **icarus** thành **verilator** `make SIM=verilator`

**Màn hình hiển thị như sau là bạn đã thành công!**
![dd28d3b858adf7f3aebc](https://github.com/dotienmanh/dotienmanh/assets/124155505/46a53873-ebb8-4db7-bd7a-109eea15d3d8)
> **Done**
