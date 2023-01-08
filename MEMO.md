IMAGE=target/thumbv7em-none-eabihf/debug/embedded_os openocd -f interface/stlink.cfg -f target/stm32f4x.cfg -c "init; reset halt; flash write_image erase $IMAGE; verify_image $IMAGE; reset; shutdown"

gdb target/thumbv7em-none-eabihf/debug/embedded_os

gdb
http://nalab.mind.meiji.ac.jp/~mk/knowhow-2018/node23.html
sudo port install gdb +multiarch
このオプションを入れないとarm macでデバッグできない

GDB には、リモートデバッグと呼ばれる機能があります。この機能を使用すると、別の環境で動いているプログラムと通信して、そのプログラムをデバッグすることができます。

例えば、あなたが試しているように、マイコンを USB 経由で接続して、そのマイコンにイメージを書き込んでデバッグする場合、マイコンを GDB のターゲットとして使用することができます。

このような場合、GDB は、お使いのコンピュータ上で実行されていますが、その GDB は、マイコンと通信して、マイコン上で動いているプログラムをデバッグすることができます。

この機能を使用するには、GDB を起動した後、次のようにします。

Copy code
(gdb) target remote :3333
このコマンドを実行することで、GDB は、ポート番号 3333 を使用して、マイコンと通信するようになります。

OpenOCD は、GDB のターゲットとして使用できる、オープンソースのハードウェアデバッグツールです。OpenOCD を使用することで、GDB を使用して、マイコンや FPGA などのハードウェアをデバッグすることができます。

OpenOCD を使用するには、まず OpenOCD のサーバを起動します。その後、GDB を起動し、GDB のターゲットとして OpenOCD を指定することで、GDB から OpenOCD を使用してデバッグを行うことができます。

詳細な手順は、OpenOCD のマニュアルを参照することで確認することができます。また、GDB のマニュアルでも、リモートデバッグの詳細について記載されているため、こちらも参照することで、より詳細な情報を確認することができます。