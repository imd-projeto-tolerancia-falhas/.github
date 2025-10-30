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
```bash
cd IMDTravel && git checkout tags/BASELINE && cd ..
cd AirlinesHub && git checkout tags/BASELINE && cd ..
cd Exchange && git checkout tags/BASELINE && cd ..
cd Fidelity && git checkout tags/BASELINE && cd ..
```
3. Subir os containers
Entre no repositório setup (onde está o docker-compose.yml) e execute:

```bash
cd setup
docker compose up -d --build
```