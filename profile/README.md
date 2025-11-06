# Projeto Tolerância a Falhas

## Passo a Passo

### 1. Clonar todos os repositórios

Clone os repositórios necessários no mesmo diretório local:

```bash
git clone https://github.com/imd-projeto-tolerancia-falhas/setup.git
git clone https://github.com/imd-projeto-tolerancia-falhas/IMDTravel.git
git clone https://github.com/imd-projeto-tolerancia-falhas/AirlinesHub.git
git clone https://github.com/imd-projeto-tolerancia-falhas/Exchange.git
git clone https://github.com/imd-projeto-tolerancia-falhas/Fidelity.git
```
Todos os repositórios devem estar no mesmo nível de pasta para que o docker-compose do projeto setup funcione corretamente.

2. Checkout para uma tag específica

BASELINE
```bash
cd IMDTravel && git checkout tags/BASELINE && cd ..
cd AirlinesHub && git checkout tags/BASELINE && cd ..
cd Exchange && git checkout tags/BASELINE && cd ..
cd Fidelity && git checkout tags/BASELINE && cd ..
```
COMFALHAS
```bash
cd IMDTravel && git checkout tags/COMFALHAS && cd ..
cd AirlinesHub && git checkout tags/COMFALHAS && cd ..
cd Exchange && git checkout tags/COMFALHAS && cd ..
cd Fidelity && git checkout tags/COMFALHAS && cd ..
```

3. Subir os containers
Entre no repositório setup (onde está o docker-compose.yml) e execute:

```bash
cd setup
docker compose up -d --build
```
4. Testar
```bash
curl --location 'http://localhost:8080/buyTicket' \
--header 'Content-Type: application/json' \
--data '{
    "user": "1",
    "flight": "AB123",
    "day": "10/12/2025"
}'
```

5. Extras

É possível configurar as falhas e mudar os valores de suas propriedades através do arquivo application.properties:

AirlinesHub
```properties
omission.probability=0.2
time.probability=0.1
time.delay.millis=5000
time.duration.millis=10000
fail.mode.flight=true
fail.mode.sell=true
```
Exchange
```properties
fail.probability=0.1
fail.time=5
fail.mode=true
```
Fidelity
```properties
crash.probability=0.02
fail.mode=true
```
