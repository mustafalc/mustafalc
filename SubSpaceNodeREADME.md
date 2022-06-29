subspace-node-TR
Subspace Network scriptli node kurulum Türkçe rehberi. ''Güncel script'' image

Öncelikle bir Subspace cüzdanına ihtiyacınız var, cüzdanız varsa bu adımı geçin.
Cüzdan kurulumu için buraya giriyoruz.

Add account diyoruz görselde ki gibi:
image

Şimdi buradaki cüzdanımızın bilgilerini kaydediyoruz ve next diyoruz:
image

Daha sonra şifre belirleyip next + save diyoruz.

Alttan hesabımızı seçip adresimizi kopyalıyoruz ve not ediyoruz:
image

Kurulum:
< node-ismi > yazan kısımlara kendi node isminizi girip yazıyoruz.

apt install screen
screen -S subNode
echo 'export SUBSPACE_NODENAME='<node-ismi> >> $HOME/.bash_profile
echo 'export SUBSPACE_WALLET='<cüzdan-adresi> >> $HOME/.bash_profile
wget -O subspace-last.sh http://api.rues.info/subspace-last.sh && chmod +x subspace-last.sh && ./subspace-last.sh
wget -O subspace-oto.sh http://api.rues.info/subspace-oto.sh && chmod +x subspace-oto.sh && ./subspace-oto.sh
journalctl -u subspaced -f -o cat
CTRL + A + D
Yararlı komutlar:
Node logları:

journalctl -u subspaced -f -o cat
Farmer ekranı:

screen -S subFarmer
journalctl -u subspaced-farmer -f -o cat
Node resetleme:

sudo systemctl restart subspaced
Reset farmer:

sudo systemctl restart subspaced-farmer
Node kaldırma:

sudo systemctl stop subspaced subspaced-farmer
sudo systemctl disable subspaced subspaced-farmer
rm -rf ~/.local/share/subspace*
rm -rf /etc/systemd/system/subspaced*
rm -rf /usr/local/bin/subspace*
Teşekkürler <3
