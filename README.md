### Hi there 👋
# Hướng dẫn cài Cocotb và chạy ví dụ
> Hướng dẫn được thực hiện trên Ubuntu 
## Bước 1: Các yêu cầu cần có trước khi cài Cocotb
### Python 3.6+
> Check version Python
```
python3 --version
```
- Nếu chưa có, hãy cài Python:
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
> Thực hiện từng bước sau
```
wget https://ftp.gnu.org/gnu/make/make-4.3.tar.gz
tar xfz make-4.3.tar.gz
cd make-4.3/
./configure
make
```
### Trình mô phỏng cho Verilog
> Should use both, Icarus is good for a quick (to start) simulation. Verilator is good for exhaustive tests.
##### Icarus Verilog
- Cài Iverilog và gtkwave
```
sudo apt install iverilog gtkwave
```

##### Verilator
- 
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
sudo ./setup.oy install
```
>Nếu báo `/usr/bin/env: python: No such file or directory`, thử chạy: `whereis python` rồi tạo liên kết đến đó `sudo ln -s/urs/bin/python/usr/bin/python`.
Sau đó chạy lại file `setup.py` tại cocotb. nếu không được hãy thử `sudo apt install python-is-python3`
- Chuyển đến mục cần chạy test
```
cd examples/adder/tests
```
- Nếu phiên bản conda >= 4.4, cần phải deactive conda environment
```
conda deactive
```
- Chọn simulator và chạy make
```
make SIM=icarus
```

> Done


<!--
**dotienmanh/dotienmanh** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
