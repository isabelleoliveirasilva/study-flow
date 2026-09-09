**REQUISITOS FUNCIONAIS**

**Cadastro e Login**

**RF01** — O sistema deve iniciar em uma landing page que explica brevemente sobre o site e conter um botão call to action para o usuário se cadastrar.  
**RF02** — O sistema deve permitir cadastro por meio de nome, email, senha e confirmação de senha. A senha deve atender a critérios mínimos de segurança (mínimo de 8 caracteres, com letras e números). O cadastro deve exigir o aceite dos Termos de Uso e da Política de Privacidade.  
**RF03** — O sistema deve enviar um código de verificação por email antes de concluir o cadastro. O código deve expirar após um tempo determinado (ex.: 15 minutos) e permitir reenvio, desabilitando o código anterior. Deve haver um limite de tentativas de envio/reenvio para evitar abuso. Um email já cadastrado e verificado não pode ser utilizado para novo cadastro. Os dados do cadastro devem ficar em estado "pendente" até a verificação ser concluída.  
**RF04** — A senha deve ser armazenada com hash irreversível (bcrypt) no banco de dados, nunca em texto puro ou de forma reversível.  
**RF05** — Após finalizar o cadastro, o usuário deve ser autenticado automaticamente.  
**RF06** — O login deve ser feito por email e senha. O sistema deve limitar tentativas de login malsucedidas (bloqueio temporário) para mitigar ataques de força bruta. Deve haver opção de manter o usuário conectado, com duração de sessão definida.  
**RF07** — O usuário deve ter uma opção para recuperar senha, informando o email cadastrado. O sistema deve enviar um link de redefinição com token de uso único e tempo de expiração definido (ex.: 30 minutos). Por segurança, a mensagem de retorno não deve indicar se o email existe ou não na base de dados.  
**RF08** — O sistema deve permitir logout, encerrando a sessão do usuário.  
**RF09** — O usuário deve poder editar informações do perfil (nome, email) e alterar a senha estando autenticado, exigindo confirmação da senha atual para a troca.  
**RF10** — O usuário deve poder excluir sua conta, com confirmação explícita antes da exclusão definitiva dos dados.  

**Dashboard**

**RF11** — A página de dashboard deve exibir um resumo geral no topo, com métricas consolidadas: tempo total estudado, frequência/constância de estudos (dias seguidos de estudo) e total de questões resolvidas.  
**RF12** — A página de dashboard deve conter um gráfico (com opção de período semanal, mensal ou 90 dias) que apresenta a relação entre os dias e horas estudadas. Caso o usuário não possua nenhuma sessão registrada, deve ser exibido um estado vazio orientando o cadastro da primeira sessão.  
**RF13** — O dashboard deve conter uma seção com uma tabela geral de análise das matérias, contendo: nome da matéria, tempo total estudado (horas e minutos), porcentagem de acerto em relação ao total de questões resolvidas, quantidade de revisões totais realizadas e um botão para análise detalhada. Caso a matéria não possua questões resolvidas, a porcentagem de acerto deve ser exibida como "—" (não calculada). Deve conter uma indicação visual clara (ex.: legenda ou título da seção) informando que os valores são totais gerais, independentes do período selecionado no gráfico do RF12, para evitar confusão entre as duas seções.  
**RF14** — O botão de análise detalhada deve abrir um pop-up com a análise da matéria selecionada, contendo os seguintes indicadores calculados individualmente:  
**RF14.1** — Relação entre tempo investido e resultado obtido (variação da % de acerto total em questões por horas totais estudadas) em comparação com todas as matérias (para informar se está na média, abaixo ou acima).  
**RF14.2** — Evolução no percentual de acerto em questões (realizar média de todas porcentagens de questões registradas e verificar se as últimas 5 resoluções estão acima, abaixo ou na média), caso não existam 5 resoluções registradas deve aparecer uma informação de “Você precisa resolver mais questões para calcular sua evolução”.  
**RF14.3** — Indicação de prioridade da matéria em relação às demais, com base em uma combinação objetiva de menor % de acerto e menor frequência de estudo total.  
**RF14.4** — Progresso em relação às metas definidas para a matéria (quando houver meta cadastrada), calculado por projeção linear entre o valor-alvo e o prazo definido na meta: comparando o progresso esperado até a data atual (proporcional ao tempo decorrido) com o progresso real registrado nas sessões da matéria desde a criação da meta. O resultado deve indicar se o aluno está dentro/acima ou abaixo do ritmo esperado, informando a diferença numérica restante para atingir a meta.  
**RF14.5** — Frequência de estudo da matéria total, com base nas sessões cadastradas.  

