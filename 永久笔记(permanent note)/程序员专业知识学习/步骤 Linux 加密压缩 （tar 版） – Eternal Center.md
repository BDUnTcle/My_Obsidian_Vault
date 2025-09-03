#Linux/命令 #Linux/Shell脚本 
- [[#^step1|步骤一：创建测试文件]]
- [[#^step2-1|步骤二：加密压缩]]
- [[#^step3-1|步骤三：解密解压]]
- [[#^chtgpt|chatgpt问答]]
### 步骤一：创建测试文件 

```shell

# touch test.txt

```

（补充：这里以创建 test.txt 文件为例） ^step1

### 步骤二：加密压缩文件或目录
#### 2.1 交互式加密压缩文件或目录 ^step2-1

```shell

# tar -zcf - test.txt | openssl des3 -salt | dd of=test1.tar.gz

enter des-ede3-cbc encryption password:

Verifying - enter des-ede3-cbc encryption password:

*** WARNING : deprecated key derivation used.

Using -iter or -pbkdf2 would be better.

0+1 records in

0+1 records out

224 bytes copied, 7.04902 s, 0.0 kB/s

```


（  

补充：  

1) 这里以将 test.txt 文件加密压缩成 test1.tar.gz （压缩）包为例  

2) 如果要以 bzip2 的格式进行压缩，则将命令中的 -zcf 换成 -jcvf 将 test1.tar.gz 换成 test1.tar.bz2  

3) 如果要以 xz 的格式进行压缩，则将命令中的 -zcf 换成 -Jcvf 将 test1.tar.gz 换成 test1.tar.xz  

） 

  

#### 2.2 非交互式加密压缩文件或目录

  

```shell

# tar -zcf - test.txt | openssl des3 -salt -k mypassword | dd of=test2.tar.gz

des3: Unrecognized flag f

des3: Use -help for summary.

0+0 records in

0+0 records out

0 bytes copied, 0.00376576 s, 0.0 kB/s

```

  

（  

补充：  

1) 这里以将 test.txt 文件加密压缩成 test1.tar.gz （压缩）包并且将密码设置为 eternalcenter 为例  

2) 如果要以 bzip2 的格式进行压缩，则将命令中的 -zcf 换成 -jcvf 将 test1.tar.gz 换成 test2.tar.bz2  

3) 如果要以 xz 的格式进行压缩，则将命令中的 -zcf 换成 -Jcvf 将 test1.tar.gz 换成 test2.tar.xz  

） ^step2-2

  

### 步骤三：解压加密文件或目录

  

#### 3.1 交互式解压加密文件或目录 ^step3-1

  

##### 3.1.1 删除原测试目录和里面的文件

  

```shell

# rm -rf test.txt

```

  

（补充：这里以删除 test.txt 文件为例）

  

##### 3.1.2 交互式解压加密文件或目录

  

```shell

# dd if=test2.tar.gz | openssl des3 -d | tar -zxf -

0+1 records in

0+1 records out

224 bytes copied, 0.000589721 s, 380 kB/s

enter des-ede3-cbc decryption password:

*** WARNING : deprecated key derivation used.

Using -iter or -pbkdf2 would be better.

```

  

（  

补充：  

1) 这里以解压 test2.tar.gz （压缩）包为例  

2) 如果是 bzip2 格式的（压缩）包，则将命令中的 -zxf 换成 -jcvf 将 test1.tar.gz 换成 test1.tar.bz2  

3) 如果是 xz 格式的（压缩）包，则将命令中的 -zxf 换成 -Jcvf 将 test1.tar.gz 换成 test1.tar.xz  

）

  

#### 3.2 非交互式解压加密文件或目录 ^step3-2

  

##### 3.2.1 删除原测试目录和里面的文件

  

```shell

# rm -rf test.txt

```

  

（补充：这里以删除 test.txt 文件为例）

  

##### 3.2.2 非交互式解压加密文件或目录

  

```shell

# dd if=test1.tar.gz | openssl des3 -d -k eternalcenter | tar zxf -

0+1 records in

0+1 records out

224 bytes copied, 0.000574539 s, 390 kB/s

*** WARNING : deprecated key derivation used.

Using -iter or -pbkdf2 would be better.

```

  

（  

补充：  

1) 这里以解压 test1.tar.gz （压缩）包并且解压密码为 eternalcenter 为例  

2) 如果是 bzip2 格式的（压缩）包，则将命令中的 -zxf 换成 -jcvf 将 test1.tar.gz 换成 test1.tar.bz2  

3) 如果是 xz 格式的（压缩）包，则将命令中的 -zxf 换成 -Jcvf 将 test1.tar.gz 换成 test1.tar.xz  

）

---
# chatgpt问答 ^chtgpt
[对应网页](https://chat.openai.com/c/6c7cabfc-d34e-4385-8178-4a7343cebcd7)

您可以使用以下命令将目录压缩并加密为一个`.tar.gz.enc`文件：

```
tar cz directory/ | openssl enc -aes-256-cbc -out filename.tar.gz.enc
```

该命令使用`tar`命令和`gzip`压缩算法将目录打包成一个`.tar.gz`文件，并使用管道将其传输给`openssl`命令进行加密。`openssl`命令使用`AES-256-CBC`加密算法加密数据，并将其输出到名为`filename.tar.gz.enc`的加密文件中。

要解密和解压缩该文件，请使用以下命令：

```
openssl enc -aes-256-cbc -d -in filename.tar.gz.enc | tar xz
```

该命令使用`openssl`命令对`.tar.gz.enc`文件进行解密，并使用管道将其输出传递给`tar`命令来解压缩数据。`-d`选项告诉`openssl`命令进行解密，`-in`选项指定要解密的加密文件的名称，`xz`选项指定`tar`命令使用`gzip`算法来解压缩数据。