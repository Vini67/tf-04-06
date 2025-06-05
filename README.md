1. Escolha do banco NoSQL
Como é um sistema de entregas com muita leitura e escrita em tempo real, o banco ideal é MongoDB (Banco de Documentos) porque:

Documentos JSON flexíveis, bons para armazenar dados heterogêneos.

Escala horizontal fácil.

Consultas rápidas e índices eficientes.

2){
  "id_entrega": "E123456",
  "id_cliente": "C78910",
  "local_origem": {
    "endereco": "Rua A, 123",
    "cidade": "São Paulo",
    "estado": "SP",
    "cep": "01234-567"
  },
  "local_destino": {
    "endereco": "Avenida B, 456",
    "cidade": "Rio de Janeiro",
    "estado": "RJ",
    "cep": "76543-210"
  },
  "status_entrega": "em trânsito",
  "data_hora_coleta": "2025-06-03T14:30:00Z",
  "data_hora_entrega": "2025-06-04T16:00:00Z"
}



2.  Escolha entre escalabilidade horizontal ou vertical
é a escalabilidade horizontal pois ela permite distribuir a carga entre vários servidores , melhorando desempenho e disponibilidade, e é mais  resiliente a falhas se um servidor cair.

2){
  "_id": "ObjectId",                
  "clienteId": "string",           
  "origem": {
    "endereco": "string",
    "latitude": "number",
    "longitude": "number"
  },
  "destino": {
    "endereco": "string",
    "latitude": "number",
    "longitude": "number"
  },
  "status": "string",             
  "dataColeta": "ISODate",        
  "dataEntrega": "ISODate"        
}



3. Escreva uma consulta (em MongoDB ou Cassandra) para buscar todas as entregas com status “em trânsito” para um determinado cliente
db.entregas.find({
  status: "em trânsito",
  clienteId: "12345"
})

2)Como otimizar essa consulta?
 Índices compostos
Criar um índice composto nos campos que você está filtrando na consulta (status e clienteId) acelera a busca, porque o MongoDB pode usar esse índice para localizar documentos rapidamente.
Exemplo:
js
Copiar
db.entregas.createIndex({ status: 1, clienteId: 1 })



4.  Liste 3 métricas críticas que você monitoraria nesse sistema em produção e explique por quê.
Latência das operações de leitura e escrita

Por quê? A latência impacta diretamente a experiência do usuário e a responsividade do sistema. Em um sistema de entregas em tempo real, atrasos podem significar informações defasadas.

 Taxa de erros 

Por quê? Monitorar falhas ajuda a detectar problemas na infraestrutura, configurações erradas ou bugs que impactam a disponibilidade e a integridade dos dados.

cUso de CPU e memória dos nós do cluster

Por quê? Para garantir que o ambiente está dimensionado corretamente e não sobrecarregado, prevenindo quedas ou lentidões causadas por falta de recursos.
