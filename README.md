1. Escolha do Banco NoSQL
Para um sistema de entregas com alta demanda de leitura e escrita em tempo real, o banco ideal é o MongoDB (Banco de Documentos), devido aos seguintes motivos:

Utiliza documentos JSON flexíveis, adequados para armazenar dados heterogêneos e aninhados.

Facilita a escalabilidade horizontal, distribuindo dados facilmente entre múltiplos servidores.

Permite consultas rápidas com índices eficientes e suporte nativo a operações complexas.

2. Modelagem da Coleção de Entregas
Exemplo de documento JSON representando uma entrega:

json
Copiar
{
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
3. Escolha da Escalabilidade
Escalabilidade Horizontal foi escolhida pois:

Permite distribuir a carga entre vários servidores, melhorando desempenho e disponibilidade.

Proporciona maior resiliência a falhas, pois se um servidor cair, os demais continuam funcionando.

É ideal para sistemas com alta demanda e grande volume de dados, como um sistema de entregas em tempo real.

4. Consulta e Otimização
Consulta para buscar entregas “em trânsito” para um cliente específico (MongoDB):
js
Copiar
db.entregas.find({
  status_entrega: "em trânsito",
  id_cliente: "12345"
}
