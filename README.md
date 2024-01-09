# NOTE
Note of SSH GPG
# SSH
· 对称加密
· 非对称加密
ssh-keygen -t (rsa,dsa,ecdsa) -P 'passphrase' -f ~/.ssh/id_rsa 
ssh user@host  ssh -p 2024 user@host #修改端口，默认80
# GPG-GNU Privacy Guard
安装 install gnupg
创建密钥 gpg --gen-key
查看列表 gpg --list-keys
导出公钥 gpg --output public.key --author --export [Email]
导入公钥 gpg --import public.key
删除公钥 gpg --delete-key Key-ID ; --delete-secret-key
备份私钥 gpg --output private.key --armor --export-secret-keys [Your-Email]
恢复私钥 gpg --import private.key
加密数据 gpg --output doc.gpg --encrypt --recipient [Recipient-Email] doc.txt
解密数据 gpg --output doc.txt --decrypt doc.gpg
创建签名 gpg --output doc.sig --detach-sig doc.txt
验证签名 gpg --verify doc.sig doc.txt
非对称加密 echo 'YourPassPhrase' | gpg --batch --yes --passphrase-fd 0 --symmetric --cipher-algo AES256 -o outputfile.gpg inputfile.tar.gz
解密 echo 'YourPassPhrase' | gpg --batch --yes --passphrase-fd 0 -o outputfile.tar.gz -d inputfile.gpg
