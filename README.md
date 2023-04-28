# ELIXIR-TESTNET2

## Elixir v2 testnet node guide

Cайт: https://elixir.finance/ 

Твиттер: https://twitter.com/ElixirProtocol 

Дискорд: https://discord.gg/hAPfBSjkCj

Минимальные системные требования:

2 CPU 4 GB RAM 40 GB SSD OS: Ubuntu 20.04

Устанавливаем нужные пакеты и обновляем "данные":

```
sudo apt-get update

sudo apt-get install 

 ca-certificates 

curl 

 gnupg 

 Lsb-release
```

Устанавливаем докер:

```
sudo mkdir -p /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

```
echo \
 "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
 $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```
sudo apt-get update
```

```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

```
sudo docker run hello-world
```

После должно отобразиться: (вводить не нужно, просто смотрим вывод и сравниваем)

```
You should see a message: 
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
2db29710123e: Pull complete
```

Смотрим запущенные контейнеры:

```
docker ps
```

Скачиваем докерфайл:

```
wget https://files.elixir.finance/Dockerfile
```

Изменяем конфигурацию:

```
apt install nano
```

```
nano Dockerfile
```

в открывшемся файде вносим изменения в 3-х местах - адрес Метамаск, приват ММ, имя ноды и сохраняем (контрл +s контрл + х)
Заполняем после равно без кавычек и пробелов. ENV ADDRESS - адрес метамаска, PRIVATE_KEY - приватный ключ (не фраза), VALIDATOR_NAME - имя валидатора.
```
FROM elixirprotocol/validator: testnet-1
ENV ADDRESS=
ENV PRIVATE_KEY=
ENV VALIDATOR_NAME=
```

Создаем образ валидатора:

```
docker build . -f Dockerfile -t elixir-validator
```

Запускаем ноду:

```
docker run -it --name ev elixir-validator
```

Посмотреть запущенные контейнеры:

```
docker container ls

docker container logs <CONTAINED_ID>
```

Создаем валидатора

Переходим на сайт - https://dashboard.elixir.finance и конектим кошелек.

Клеймим тестовые токены ELXR (нужен тестовый эфир чтобы заклеймить, можно запросить в канале https://discord.gg/hAPfBSjkCj ).

После того, как вы получили токены ELXR, стейкаем токены. Подойдет любая сумма от 100–1000 ELXR.

Затем зарегистрируйте валидатора. Вы можете нажать кнопку регистрации, а затем ввести адрес кошелька, который использовался для запуска валидатора на предыдущих шагах.

 Может быть задержка, прежде чем кнопка регистрации станет активной.

Как только эта транзакция будет подтверждена, проверьте таблицу лидеров, чтобы убедиться, что ваш адрес зарегистрирован.

Затем убедитесь, что действительные заказы обрабатываются, найдя свой валидатор на странице метрик.

Мой Ютуб

https://www.youtube.com/channel/UCM3eD0Rh3a52c6NoFeCCYzg
