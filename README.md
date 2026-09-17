# Entrega 1 — Modelo Conceitual (DER)
### Modelagem de um sistema de gestão de informações para uma organização de pequeno porte

---

## Metadados

- **Nomes dos alunos e RGM:** 

---

## 1. Caracterização da Organização

- **Nome e natureza da organização:** Clínica Sued Odontologia Humanizada — clínica odontológica particular, com fins lucrativos, atualmente em processo de implantação de atendimento por convênio (1 convênio).
- **Contexto e porte:** clínica em funcionamento há 6 meses. Estrutura enxuta: 1 sala de atendimento e 1 funcionária (a própria dentista responsável, Tamires, que também acumula a função de recepção/agendamento). Atende cerca de 20 pacientes cadastrados, com uma média de 7 atendimentos por semana. Os serviços oferecidos incluem atendimento clínico geral, implantes e próteses, além de outros procedimentos como limpeza, cirurgia, endodontia e clareamento.
- **Problemas e necessidades identificados:** as informações da clínica hoje estão divididas entre um aplicativo criado com apoio de IA e fichas clínicas físicas. O prontuário do paciente é mantido apenas em papel (ficha física + ficha de evolução), o que dificulta a consulta rápida do histórico. O agendamento é feito manualmente via WhatsApp e conferido no Google Agenda, sem sistema de bloqueio automático de horários. Não há controle financeiro sistematizado — o pagamento não é registrado em nenhum sistema, apenas mencionado no prontuário físico. Também não existe controle formal de estoque de materiais. A dona relatou como maior necessidade ter um "prontuário eletrônico" e otimizar a busca de pacientes e o controle financeiro.
- **Justificativa da escolha:** a clínica é pequena o suficiente para ser modelada nesta etapa (poucos profissionais, processos ainda simples), mas já gera entidades e relacionamentos suficientes para um modelo relevante: pacientes, dentistas, agendamentos, atendimentos, procedimentos, tratamentos e pagamentos. Além disso, por ser uma operação recém-criada e ainda sem sistema informatizado estruturado, o grupo tem espaço real para propor melhorias que a própria clínica já demonstrou desejar (prontuário eletrônico, busca rápida, controle financeiro).
- **Evidências da organização:**
  - **Endereço:** Praça Nelson Sales de Abreu, 103 - Sl 04, Cidade Patriarca, São Paulo - SP, CEP 03547-100
  - **Telefone de contato:** (11) 95387-7504
  - **Localização no Google Maps:** [maps.app.goo.gl/E1UdxAZoc6zMUEYx5](https://maps.app.goo.gl/E1UdxAZoc6zMUEYx5)
  - **Responsável pela organização:** Tamires (dentista e proprietária da clínica)
  - **Foto da visita de campo:**

    ![Foto da visita à Clínica Sued Odontologia Humanizada](imagens/foto_visita.jpg)

---

## 2. Processos de Negócio

**Principais processos mapeados:**

1. **Cadastro de paciente** — feito por meio de anamnese física no primeiro atendimento; coleta dados pessoais e informações de saúde relevantes. Nome e telefone são obrigatórios; o paciente pode ter mais de um telefone de contato. O cadastro pode ser alterado posteriormente.
2. **Agendamento de consulta** — o paciente entra em contato via WhatsApp (é o único canal, exceto presencialmente com agendamento prévio); a própria dentista realiza o agendamento, verificando disponibilidade no Google Agenda. Em caso de cancelamento, é oferecido reagendamento; em caso de falta, a clínica entra em contato para saber o motivo e reagendar.
3. **Atendimento** — o paciente é recepcionado e avaliado pela própria dentista, que confirma a chegada. Durante o atendimento são registrados os procedimentos realizados e observações. Um atendimento pode envolver mais de um procedimento.
4. **Acompanhamento de tratamento** — quando o paciente precisa de múltiplos atendimentos ao longo do tempo (ex.: tratamento de canal, implante), a evolução é registrada em uma ficha de evolução física.
5. **Pagamento** — pode ocorrer antes ou depois do atendimento, à vista ou parcelado, em pix, crédito, débito ou dinheiro. Não há registro sistematizado — o controle é feito apenas por meio do prontuário físico.
6. **(Processo em implantação) Convênios** — a clínica está iniciando o atendimento por convênio; as regras específicas (autorização de procedimentos, múltiplos convênios por paciente etc.) ainda não estão consolidadas.


---

## 3. Requisitos do Sistema

### 3.1 Requisitos Funcionais

- RF01 — O sistema deve permitir cadastrar pacientes com, no mínimo, nome e telefone, admitindo mais de um telefone por paciente.
- RF02 — O sistema deve permitir registrar e consultar o histórico completo de atendimentos de um paciente.
- RF03 — O sistema deve permitir agendar consultas associando paciente, dentista, data e horário, impedindo que dois pacientes sejam agendados no mesmo horário com o mesmo dentista.
- RF04 — O sistema deve permitir marcar o status de um agendamento (confirmado, cancelado, remarcado, não compareceu).
- RF05 — O sistema deve permitir registrar um atendimento vinculado a um ou mais procedimentos realizados.
- RF06 — O sistema deve permitir cadastrar procedimentos com preço base, número estimado de sessões e, quando aplicável, procedimento(s) pré-requisito(s).
- RF07 — O sistema deve permitir agrupar atendimentos de um mesmo paciente em um tratamento, com acompanhamento de evolução.
- RF08 — O sistema deve permitir registrar pagamentos vinculados a um atendimento, admitindo múltiplos pagamentos (parcelamento) e múltiplas formas de pagamento.
- RF09 — O sistema deve permitir identificar pagamentos pendentes.
- RF10 — O sistema deve permitir cadastrar dentistas com uma ou mais especialidades.
- RF11 — O sistema deve permitir buscar rapidamente um paciente pelo nome ou telefone.

### 3.2 Requisitos Não Funcionais

- RNF01 — **Usabilidade:** interface simples, já que o sistema será operado por uma única profissional sem apoio técnico dedicado.
- RNF02 — **Segurança e privacidade:** acesso às informações do paciente deve ser restrito à dentista responsável (ou a quem ela autorizar), dado o caráter sensível dos dados de saúde.
- RNF03 — **Disponibilidade:** o sistema deve estar acessível também por dispositivo móvel, já que o agendamento hoje é feito por WhatsApp fora do horário fixo de clínica.
- RNF04 — **Desempenho:** buscas de paciente e consulta de dados financeiros devem retornar resultados rapidamente, atendendo à necessidade relatada de "otimizar a busca de pacientes e financeiro".
- RNF05 — **Confiabilidade:** os dados de prontuário não podem ser perdidos, dado que hoje existe dependência de ficha física.

---

## 4. Regras de Negócio

**Regras operacionais:**

- Um paciente só pode ser cadastrado com, no mínimo, nome e telefone preenchidos.
- Um mesmo horário não pode ter dois pacientes agendados com o mesmo dentista (exclusividade horário × dentista).
- Um dentista pode ter várias consultas marcadas no mesmo dia.
- Caso o procedimento necessário exija uma especialidade diferente da dentista titular, o paciente é encaminhado a um dentista parceiro.
- Um procedimento pode exigir a realização prévia de outro procedimento (ex.: pré-requisito clínico antes de um implante).
- O preço de um procedimento é variável e pode mudar conforme o paciente ou a situação clínica.
- Um atendimento pode ser pago em mais de uma vez (parcelamento), inclusive combinando formas de pagamento diferentes.
- O pagamento pode ocorrer antes ou depois do atendimento.
- Quando há pagamento pendente, a clínica notifica o paciente.
- Em caso de cancelamento, é oferecido reagendamento; em caso de falta, a clínica contata o paciente para entender o motivo e propor novo horário.

**Restrições organizacionais:**

- A estrutura atual (1 sala, 1 dentista fixa) limita a quantidade de atendimentos simultâneos — isso importa para o modelo porque não há, hoje, necessidade de representar múltiplas salas ou múltiplos atendimentos simultâneos, mas o modelo deve permitir essa expansão futura.
- O atendimento por convênio está em fase de implantação; as regras específicas (autorização, múltiplos convênios por paciente) ainda não estão definidas na prática, então o modelo trata essa entidade de forma mais enxuta, pensando em expansão posterior.
- O acesso às informações do paciente é hoje restrito exclusivamente à dentista — restrição de privacidade que deve ser preservada no sistema.
- Não existe, atualmente, identificador único formal por paciente (a identificação é feita por nome) — isso é um risco de duplicidade que o modelo corrige ao propor uma chave primária gerada pelo sistema.

---

## 5. Dicionário de Dados Conceitual (Preliminar)

O dicionário de dados completo — com todos os atributos de cada entidade (Paciente, Dentista, Agendamento, Atendimento, Procedimento, Tratamento e Pagamento), suas descrições e as regras de negócio associadas — está disponível no arquivo HTML anexado a este repositório:

📄 **[Dicionário de Dados (HTML)](LINK_DO_ARQUIVO_AQUI)**

> Os valores de exemplo usados no dicionário são **fictícios**, usados apenas para ilustrar o tipo de dado — nenhum paciente ou dentista real é citado.

---

## 6. Modelagem Conceitual (Entidades, Atributos, Relacionamentos)

**Entidades reconhecidas:** Paciente, Dentista, Agendamento, Atendimento, Procedimento, Tratamento e Pagamento, além da entidade associativa Atendimento_Procedimento (para representar o relacionamento N:M entre atendimento e procedimento, com preço praticado naquele caso específico).

**Relacionamentos pertinentes:**

- **Paciente — Agendamento:** um paciente pode ter vários agendamentos (1:N); um agendamento pertence a um único paciente.
- **Dentista — Agendamento:** um dentista pode ter vários agendamentos (1:N); um agendamento é feito com um único dentista.
- **Agendamento — Atendimento:** um agendamento dá origem a, no máximo, um atendimento efetivo (1:1 opcional, já que agendamentos podem ser cancelados ou resultar em falta).
- **Paciente — Atendimento:** um paciente pode ter vários atendimentos ao longo do tempo (1:N).
- **Dentista — Atendimento:** um dentista realiza vários atendimentos (1:N); como um paciente pode ser atendido por dentistas diferentes conforme a especialidade necessária, a relação paciente–dentista, no todo, é N:M, materializada através da entidade Atendimento.
- **Atendimento — Procedimento (via Atendimento_Procedimento):** um atendimento pode envolver vários procedimentos, e um procedimento pode aparecer em vários atendimentos (N:M), com o preço efetivamente praticado registrado na entidade associativa.
- **Procedimento — Procedimento:** auto-relacionamento opcional representando o pré-requisito entre procedimentos.
- **Paciente — Tratamento:** um paciente pode ter vários tratamentos ao longo do tempo (1:N).
- **Tratamento — Atendimento:** um tratamento agrupa vários atendimentos (1:N), permitindo acompanhar a evolução de procedimentos que exigem múltiplas sessões.
- **Atendimento — Pagamento:** um atendimento pode ter vários pagamentos (1:N), suportando parcelamento e pagamentos combinados.

**Restrições e políticas organizacionais aplicadas ao modelo:**

- Exclusividade de horário por dentista (um horário não comporta dois pacientes com o mesmo profissional).
- Cadastro mínimo obrigatório de paciente (nome e telefone).
- Acesso à informação do paciente restrito à dentista responsável.

---

## 7. Diagrama Entidade-Relacionamento (DER)

*[Anexar aqui a imagem do DER, elaborado a partir das entidades, atributos, relacionamentos e cardinalidades descritos nas Seções 5 e 6]*

O diagrama deve representar todas as entidades listadas na Seção 6, seus atributos (incluindo a identificação das chaves primárias e do atributo multivalorado `especialidade` em Dentista), os relacionamentos descritos e as cardinalidades levantadas junto à clínica (1:N entre Paciente/Dentista e Agendamento/Atendimento; N:M entre Atendimento e Procedimento; 1:N entre Tratamento e Atendimento; 1:N entre Atendimento e Pagamento).

---

## 8. Justificativa Técnica

- **Separação entre Agendamento e Atendimento:** optou-se por não unificar essas duas entidades porque a clínica relatou casos de cancelamento e falta — ou seja, nem todo agendamento se converte em atendimento efetivo. Manter as duas entidades separadas permite registrar esse histórico sem perder informação.
- **Entidade associativa Atendimento_Procedimento:** como um atendimento pode envolver vários procedimentos e o preço de um procedimento pode variar de paciente para paciente, uma relação simples 1:N não seria suficiente — a entidade associativa permite registrar o preço efetivamente praticado em cada combinação específica de atendimento e procedimento.
- **Entidade Tratamento separada de Atendimento:** a clínica relatou acompanhar a "evolução" de procedimentos que exigem várias sessões (ex.: endodontia, implante) por meio de uma ficha de evolução física. Modelar Tratamento como agrupador de vários Atendimentos reproduz esse processo real e permite consultar a evolução de forma estruturada, em vez de tratar cada visita como um evento isolado.
- **Auto-relacionamento em Procedimento:** a entrevista indicou explicitamente que existem procedimentos que exigem outro procedimento antes. Um auto-relacionamento é a forma mais direta de capturar essa dependência sem duplicar entidades.
- **Pagamento como entidade própria, e não atributo de Atendimento:** como um atendimento pode ser pago em mais de uma vez e com formas diferentes, tratar pagamento como atributo simples do atendimento impediria representar parcelamento. Uma entidade própria, relacionada 1:N ao atendimento, resolve isso.
- **Identificadores únicos (id_paciente, id_dentista etc.):** a clínica não possui hoje nenhum identificador único por paciente, usando o nome como referência — o que é um risco real de duplicidade e ambiguidade (dois pacientes podem ter o mesmo nome). A introdução de chaves primárias geradas pelo sistema resolve esse problema sem alterar o processo de atendimento da clínica.
- **Convênio tratado de forma enxuta:** como o atendimento por convênio ainda está sendo implantado e suas regras não estão consolidadas na prática, optou-se por não detalhar essa entidade nesta etapa, para não modelar regras hipotéticas. Isso deixa o modelo mais fiel à realidade atual, mas já demonstra potencial de escalabilidade para incorporar convênio(s) por paciente nas próximas etapas do projeto.

---

## 9. Uso de Inteligência Artificial

| Item | Registro |
|------|------------------|
| **Ferramenta e etapa** | Claude (Anthropic) — utilizado na organização das respostas da entrevista de campo e na redação do README (caracterização da organização, requisitos, regras de negócio, dicionário de dados, modelagem conceitual e justificativa técnica). |
| **Motivação** | O grupo já havia realizado a entrevista presencial na clínica e precisava estruturar as respostas no formato exigido pelo esqueleto do README, incluindo a identificação de entidades, atributos e cardinalidades a partir das respostas obtidas. |
| **Prompt(s) utilizados** | *[preencher com o texto exato ou muito próximo dos prompts enviados — ex.: "vc pode me ajudar em um trabalho... eu vou te enviar a entrevista que eu fiz com a empresa e vc me fala as informações que vc precisa" e, em seguida, o envio do PDF da entrevista pedindo a montagem do README]* |
| **Resposta recebida** | A IA solicitou inicialmente as informações necessárias (nome/tipo da organização, evidências de existência, processos, regras e dados coletados) e, após o envio da entrevista, gerou uma proposta de README completo, incluindo entidades, atributos, relacionamentos e cardinalidades derivados das respostas da entrevista. |
| **Fontes consultadas e verificadas** | Nenhuma fonte externa foi usada — todo o conteúdo foi derivado exclusivamente das respostas da entrevista de campo feita pelo próprio grupo na clínica. |
| **Trechos rejeitados ou corrigidos** | *[preencher — descrever o que o grupo revisou, ajustou ou removeu do texto gerado, comparando com o que foi observado na visita. Ex.: eventuais atributos sugeridos que não correspondem à realidade da clínica]* |
| **Justificativa da escolha final** | *[preencher — por que o grupo manteve, adaptou ou rejeitou o que foi sugerido]* |
| **Reflexão crítica** | A IA não teve acesso direto à clínica, apenas ao texto da entrevista — por isso, atributos como `data_nascimento` e `id_paciente` foram propostos como recomendações de boas práticas de modelagem, não como dados hoje efetivamente coletados pela clínica, e devem ser validados pelo grupo. Há também risco de a IA ter generalizado processos comuns a clínicas odontológicas que não necessariamente se aplicam a esta clínica específica (ex.: regras de convênio, que ainda estão em implantação e não foram detalhadas na entrevista). |

*(Se o grupo utilizou IA em outras etapas — como na elaboração das perguntas da própria entrevista — adicionar uma linha/tabela extra registrando esse uso também.)*

---

## Resumo dos Pesos

| Dimensão | Peso total |
|----------|-----------|
| Conceitual (contexto, requisitos/regras, modelagem, justificativa técnica) | 30% |
| Procedimental (requisitos, fluxogramas, dicionário de dados, DER) | 50% |
| Atitudinal (participação, comprometimento, colaboração, autonomia) | 20% |

**Entrega final:** README.md completo + DER + Dicionário de Dados em HTML (com exceção dos cursos GTI) anexado no repositório GitHub do grupo.
