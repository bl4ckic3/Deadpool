Usage
-----

Faulting multiple times the tables requires many disk writes so we'll do it in a tmpfs.  
All steps are performed by ```mount_tmp_and_attack.sh```:

```bash
mkdir -p tmp
mount|grep -q $(pwd)/tmp || sudo mount -t tmpfs -o mode=01777,size=20m tmpfs tmp
cp attack_owb_chow.py ../../deadpool_dfa.py ../../../JeanGrey/phoenixAES.py tmp
cp ../target/encryptECB tmp
cp ../target/key.txt tmp/key.txt.gold
cd tmp
./attack_owb_chow.py
```

Adapt it to your setup if needed. It requires ```deadpool_dfa.py``` from this repository and ```phoenixAES.py``` from [JeanGrey repository](https://github.com/SideChannelMarvels/JeanGrey).
