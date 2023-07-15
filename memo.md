
### ■ 検証用環境の準備
$ python3 -m env env
$ source venv/bin/activate
(venv) $ pip3 install pycryptodome

### ■ 検証要ファイルの作成
(venv) $ touch rsa_test.py

'''rsa_test.py
from Crypto.Util.number import long_to_bytes

p = 99989
q = 99991

'''

### ■ 検証

### ■ 検証用環境の削除
(venv) $ deactivate
$ rm -r venv
$ rm rsa_test.py