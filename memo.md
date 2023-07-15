
### ■ 検証用環境の準備
$ python3 -m env env
$ source venv/bin/activate
(venv) $ pip3 install pycryptodome


### ■ 検証要ファイルの作成
(venv) $ touch rsa_test.py

```rsa_test.py
from Crypto.Util.number import getPrime, bytes_to_long, long_to_bytes

# 暗号化対象メッセージ
msg = b"RSA_TEST"

# 暗号化／復号用パラメータ
p = getPrime(512)
q = getPrime(512)
N = p * q
e =  65537
phi = (p - 1) * (q - 1)
d = pow(e, -1, phi)

# 暗号化
msg = bytes_to_long(msg)
enc = pow(msg, e, N)
print(f"\n{enc = }")

# 復号
msg = pow(enc, d, N)
msg = long_to_bytes(msg)
print(f"\n{msg = }")
```

  
### ■ 検証
(venv) $ python3 rsa_test.py
  
  
### ■ 検証用環境の削除
(venv) $ deactivate  
$ rm -r venv  
$ rm rsa_test.py  