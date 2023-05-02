# Elixir Kurulum Rehberi

![kapak](https://user-images.githubusercontent.com/111747226/235793482-bc0c1ab6-a18b-4c84-abf8-89714e9f2dd1.jpg)



## Sistem gereksinimleri:

- **Ubuntu 20.04+**

NODE TİPİ | CPU     | RAM      | SSD     |
| ------------- | ------------- | ------------- | -------- |
| Nibiru | 1         | 2       | 30  |
  
  

- **Gerekli Güncellemeler ve Kurulum**

```
sudo apt-get update
sudo apt-get install \
   ca-certificates \
   curl \
   gnupg \
   Lsb-release
```

Devam ediyoruz;

```
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```


```
echo \
 "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
 $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```


- **Sistem Güncellemesi Yapıyoruz.**

```
sudo apt-get update
```
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
* Gelen ekrandaki uyarılara y ENTER basıp devam ediyoruz. 
```
sudo docker run hello-world
```


- **Aşağıdaki gibi bir bildirim alacaksınız.**
* Bunu terminale yazmıyoruz!!!!
```
You should see a message: 
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
2db29710123e: Pull complete
```

- **Dockerı Çalıştırıyoruz.**

```
docker ps
```
![1_ZaUmDxJl02dOyoRJkKGppA](https://user-images.githubusercontent.com/111747226/235794407-6b5a1586-b16f-4106-a3a8-2219edb8c971.jpg)

- **Metamask Cüzdan Ayarları**
![metamask](https://user-images.githubusercontent.com/111747226/214062437-69e144d9-528f-4a17-b46a-a747c1d5284c.png)
* Metmask adresimizi ve private key anahtarımızı görseldeki gibi alıp bir yere not edelim.



- **Elixir Node Kurulumu**

 
```
wget https://files.elixir.finance/Dockerfile
```

- **Dockerfile'ı cüzdan bilgilerinizle kuruyoruz**

```
nano Dockerfile
```

- **Yapılandırma ayarlarını giriyoruz.*

```
FROM elixirprotocol/validator:testnet-2
ENV ADDRESS=BURAYA CÜZDAN ADRESİ BURAYA EKLENECEK (0x ile geliyor silip cüzdan adresinizi ekleyebilirsiniz.)
ENV PRIVATE_KEY=BURAYA PRIVATE KEY BURAYA EKLİYORUZ.(0x olarak geliyor onu silmeden ekliyoruz.)
ENV VALIDATOR_NAME=İSTEDİĞİNİZ BİR AD GİREBİLİRSİNİZ. 
```
* Yukarıdaki bilgileri girdikten sonra, Ctrl + x ardından y ENTER yaparak kayıt ediyoruz.

- **Docker Kurulumunu tamamlıyoruz.**

```
docker build . -f Dockerfile -t elixir-validator
```

- **Docker Çalıştırıyoruz.**

```
docker run -it --name ev elixir-validator
```
[BURADAN](https://dashboard.elixir.finance/) platforma ulaşıyoruz. Goerli ETH ağında cüzdanımızı bağlyoruz.
![dashboard](https://user-images.githubusercontent.com/111747226/235796224-1ef3ce9d-2e40-4e90-a404-d582922215bf.jpg)


1. Adımda test tokenlerini claim ediyoruz.
2. Stake butonuna basıyoruz. Aldığımız test tokenleri stake ediyoruz. 
3. Enroll tuşuna basıyoruz ve Miktar seçip node'muza ekliyoruz ve işlemler tamamdır.

