
### ■ 検証用環境の準備
$ python3 -m env env  
$ source venv/bin/activate  
(venv) $ pip3 install pycryptodome  

<br />

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
print(f"{enc = }")

# 復号
msg = pow(enc, d, N)
msg = long_to_bytes(msg)
print(f"{msg = }")
```

<br />

### ■ 検証
(venv) $ python3 rsa_test.py  
```
# 出力結果
enc = 23613155421069822714925250448732012860050068963740946854969254346405862403566028306476879332170053140821462773901859764120144030158963889766076225742727243114011511449904397034240654599809027326794609053029981550440241935490230603557775349264603908429574522496268958660633740416304452843935975618348412115516
msg = b'RSA_TEST'
```

<br />  

### ■ 検証用環境の削除
(venv) $ deactivate  
$ rm -r venv  
$ rm rsa_test.py  