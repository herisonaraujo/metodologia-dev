# Checklist de Entrega

Este template serve para validar uma entrega digital antes, durante e depois do deploy.

O objetivo é reduzir falhas, evitar retrabalho e garantir que a solução esteja minimamente pronta para uso real.

---

## 1. Informações do projeto

**Nome do projeto:**

```md
Digite aqui o nome do projeto.
```

**Responsável:**

```md
Nome do responsável pela entrega.
```

**Data prevista de entrega:**

```md
DD/MM/AAAA
```

**Ambiente de produção:**

```md
URL do projeto em produção.
```

---

## 2. Antes de iniciar

Validação inicial de contexto, escopo e riscos.

```md
- [ ] Objetivo do projeto documentado.
- [ ] Usuários principais identificados.
- [ ] Fluxo principal definido.
- [ ] Regras de negócio documentadas.
- [ ] Integrações necessárias mapeadas.
- [ ] Restrições conhecidas registradas.
- [ ] Riscos iniciais identificados.
- [ ] Critérios de sucesso definidos.
```

---

## 3. Planejamento da entrega

```md
- [ ] Primeira entrega funcional definida.
- [ ] Prioridades organizadas.
- [ ] Pendências críticas separadas de melhorias futuras.
- [ ] Responsáveis definidos.
- [ ] Dependências externas mapeadas.
- [ ] Prazo revisado com base no escopo real.
```

---

## 4. Desenvolvimento

```md
- [ ] Interface principal criada.
- [ ] Fluxo principal funcionando.
- [ ] API principal funcionando.
- [ ] Banco de dados configurado.
- [ ] Painel administrativo criado, quando aplicável.
- [ ] Permissões básicas implementadas.
- [ ] Estados principais do processo implementados.
- [ ] Integrações principais conectadas.
- [ ] Tratamento de erros comuns implementado.
- [ ] Mensagens para o usuário revisadas.
```

---

## 5. Painel administrativo

Use esta seção quando o projeto tiver gestão interna, operação ou backoffice.

```md
- [ ] Login administrativo funcionando.
- [ ] Perfis de acesso definidos.
- [ ] Cadastro e edição de informações funcionando.
- [ ] Listagem de registros funcionando.
- [ ] Filtros ou buscas principais funcionando.
- [ ] Atualização de status funcionando.
- [ ] Exclusão ou inativação validada.
- [ ] Operação consegue executar o fluxo sem depender do desenvolvedor.
```

---

## 6. Dados e regras de negócio

```md
- [ ] Campos obrigatórios validados.
- [ ] Regras críticas implementadas.
- [ ] Exceções consideradas.
- [ ] Dados inválidos tratados.
- [ ] Estados do processo testados.
- [ ] Permissões testadas.
- [ ] Dados sensíveis revisados.
- [ ] Informações desnecessárias removidas.
```

---

## 7. Integrações

Marque apenas o que for aplicável.

### Pagamentos

```md
- [ ] Integração Pix configurada.
- [ ] Fluxo de pagamento testado.
- [ ] Status de pagamento atualizado corretamente.
- [ ] Erros de pagamento tratados.
- [ ] Comprovantes ou registros organizados.
```

### E-mail e notificações

```md
- [ ] Roteamento de e-mails configurado.
- [ ] Envio de e-mails testado.
- [ ] Notificações importantes configuradas.
- [ ] Mensagens revisadas.
- [ ] Remetente validado.
```

### Mapas e logística

```md
- [ ] Mapa carregando corretamente.
- [ ] Localização sendo capturada, quando aplicável.
- [ ] Rastreamento testado.
- [ ] Empresa consegue acompanhar a entrega.
- [ ] Cliente consegue acompanhar a entrega.
- [ ] Permissão de localização validada no celular.
```

### APIs externas

```md
- [ ] Endpoint validado.
- [ ] Token ou chave configurada.
- [ ] Erros de API tratados.
- [ ] Tempo de resposta aceitável.
- [ ] Dados recebidos conferidos.
```

### IA e automações

```md
- [ ] Objetivo da automação definido.
- [ ] Contexto usado pela IA revisado.
- [ ] Regras do agente documentadas.
- [ ] Dados sensíveis protegidos.
- [ ] Respostas ou ações validadas.
- [ ] Automação testada com cenários reais.
```

---

## 8. Qualidade visual e experiência

```md
- [ ] Layout revisado no desktop.
- [ ] Layout revisado no celular.
- [ ] Navegação principal testada.
- [ ] Botões e links funcionando.
- [ ] Textos revisados.
- [ ] Imagens otimizadas.
- [ ] Contraste visual adequado.
- [ ] Páginas de erro ou estados vazios tratados.
- [ ] Experiência do usuário compreensível.
```

---

## 9. Responsividade

```md
- [ ] Testado em celular.
- [ ] Testado em tablet, quando aplicável.
- [ ] Testado em desktop.
- [ ] Menus funcionando.
- [ ] Cards, tabelas e formulários ajustados.
- [ ] Nenhum conteúdo importante cortado.
```

---

## 10. Segurança e LGPD

```md
- [ ] Dados pessoais revisados.
- [ ] Dados sensíveis minimizados.
- [ ] Permissões de acesso validadas.
- [ ] Informações internas protegidas.
- [ ] Variáveis de ambiente não expostas.
- [ ] Chaves de API fora do código público.
- [ ] Páginas legais revisadas, quando aplicável.
- [ ] Política de privacidade incluída, quando aplicável.
- [ ] Termos de uso incluídos, quando aplicável.
```

---

## 11. Infraestrutura e deploy

```md
- [ ] Build realizado com sucesso.
- [ ] Deploy publicado.
- [ ] Domínio configurado.
- [ ] DNS validado.
- [ ] SSL ativo.
- [ ] Redirecionamentos funcionando.
- [ ] Variáveis de ambiente configuradas.
- [ ] Logs básicos disponíveis.
- [ ] Backup ou exportação avaliada.
- [ ] Ambiente de produção validado.
```

---

## 12. Testes práticos

### Fluxo principal

```md
- [ ] Usuário consegue iniciar o fluxo.
- [ ] Usuário consegue concluir o fluxo.
- [ ] Sistema registra a ação corretamente.
- [ ] Operação consegue visualizar o resultado.
- [ ] Status ou retorno é exibido corretamente.
```

### Casos de erro

```md
- [ ] Campo obrigatório vazio.
- [ ] Pagamento não confirmado.
- [ ] Produto indisponível.
- [ ] Erro de API.
- [ ] Usuário sem permissão.
- [ ] Falha de conexão.
```

### Operação interna

```md
- [ ] Operação consegue acessar o painel.
- [ ] Operação consegue alterar informações.
- [ ] Operação consegue acompanhar status.
- [ ] Operação sabe o que fazer em cada etapa.
- [ ] Operação tem instrução mínima para uso.
```

---

## 13. Documentação mínima

```md
- [ ] Objetivo do projeto documentado.
- [ ] Fluxo principal documentado.
- [ ] Regras críticas documentadas.
- [ ] Acessos necessários registrados.
- [ ] Variáveis de ambiente listadas.
- [ ] Integrações documentadas.
- [ ] Como operar o painel documentado.
- [ ] Próximos passos registrados.
```

---

## 14. Critérios para liberar produção

A entrega só deve ser considerada pronta quando:

```md
- [ ] O fluxo principal funciona de ponta a ponta.
- [ ] A operação consegue usar sem depender do desenvolvedor.
- [ ] Não há erro crítico conhecido.
- [ ] Dados sensíveis foram revisados.
- [ ] Domínio, SSL e deploy estão funcionando.
- [ ] Documentação mínima foi entregue.
- [ ] Próximos passos estão claros.
```

---

## 15. Pós-entrega

```md
- [ ] Feedback inicial coletado.
- [ ] Problemas reais registrados.
- [ ] Ajustes priorizados.
- [ ] Backlog atualizado.
- [ ] Documentação revisada.
- [ ] Melhorias futuras separadas da entrega atual.
- [ ] Responsável pela continuidade definido.
```

---

## 16. Registro de pendências

| Pendência | Impacto | Prioridade | Responsável | Status |
|---|---|---|---|---|
| | | | | |
| | | | | |
| | | | | |

---

## 17. Resumo da entrega

```md
A entrega contempla [resumo da solução], com os fluxos principais de [fluxos entregues].

Foram validados [principais validações] e ficaram como próximos passos [pendências ou melhorias futuras].

Status final: [pronto para produção / pronto com ressalvas / precisa de ajustes].
```

---

## Status final

```md
- [ ] Pronto para produção.
- [ ] Pronto com ressalvas.
- [ ] Precisa de ajustes antes de publicar.
```
