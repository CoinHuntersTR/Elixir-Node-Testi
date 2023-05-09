

# 1) Güncelleme için bu komuları giriyoruz.
  - Aşağıdaki komutları sırasıyla giriyoruz.

```
docker kill ev
```
```
docker rm ev
```
```
docker pull elixirprotocol/validator:testnet-2
```
```
docker build . -f Dockerfile -t elixir-validator
```
```
docker run -d --restart unless-stopped --name ev elixir-validator
```

  
