# Regras de Negócio

Este template serve para documentar regras, estados, permissões e exceções de um produto digital antes ou durante o desenvolvimento.

O objetivo é transformar decisões operacionais em regras claras, rastreáveis e fáceis de validar.

---

## 1. Projeto

**Nome do projeto:**

```md
Digite aqui o nome do projeto.
```

**Descrição breve:**

```md
Descreva em uma frase o que o projeto faz.
```

---

## 2. Entidades principais

Liste os elementos centrais do sistema.

```md
- Usuário:
- Cliente:
- Pedido:
- Produto:
- Pagamento:
- Entrega:
- Administrador:
- Operação:
- Motoboy/entregador:
- Outros:
```

---

## 3. Estados do processo

Descreva os status ou etapas principais do fluxo.

**Exemplo para delivery:**

```md
Pedido criado
Pedido aguardando pagamento
Pedido pago
Pedido em preparo
Pedido pronto para retirada
Pedido saiu para entrega
Pedido entregue
Pedido cancelado
```

**Estados do projeto:**

```md
1.
2.
3.
4.
5.
6.
```

---

## 4. Permissões

Defina quem pode visualizar, editar, excluir ou executar ações dentro do sistema.

| Perfil | Pode ver | Pode editar | Pode excluir | Observações |
|---|---|---|---|---|
| Administrador | | | | |
| Operação | | | | |
| Cliente | | | | |
| Motoboy/entregador | | | | |
| Gestor | | | | |
| Outro | | | | |

---

## 5. Regras

### Regra 1

**Descrição:**

```md
Explique a regra.
```

**Condição:**

```md
Quando essa regra se aplica?
```

**Ação esperada:**

```md
O que o sistema ou a operação deve fazer?
```

**Exceção:**

```md
Existe algum caso em que a regra muda?
```

---

### Regra 2

**Descrição:**

```md
Explique a regra.
```

**Condição:**

```md
Quando essa regra se aplica?
```

**Ação esperada:**

```md
O que o sistema ou a operação deve fazer?
```

**Exceção:**

```md
Existe algum caso em que a regra muda?
```

---

### Regra 3

**Descrição:**

```md
Explique a regra.
```

**Condição:**

```md
Quando essa regra se aplica?
```

**Ação esperada:**

```md
O que o sistema ou a operação deve fazer?
```

**Exceção:**

```md
Existe algum caso em que a regra muda?
```

---

## 6. Regras por área

### Produtos ou catálogo

```md
- 
- 
- 
```

### Pedidos ou solicitações

```md
- 
- 
- 
```

### Pagamentos

```md
- 
- 
- 
```

### Entrega ou logística

```md
- 
- 
- 
```

### Usuários e permissões

```md
- 
- 
- 
```

### Comunicação e notificações

```md
- 
- 
- 
```

---

## 7. Notificações

Defina quando uma notificação deve ser enviada, para quem e por qual canal.

| Evento | Quem recebe | Canal | Mensagem ou ação |
|---|---|---|---|
| Pedido criado | | | |
| Pagamento confirmado | | | |
| Pedido saiu para entrega | | | |
| Pedido entregue | | | |
| Pedido cancelado | | | |
| Erro operacional | | | |

---

## 8. Casos de erro

Liste situações que podem dar errado e o comportamento esperado.

| Erro ou exceção | Impacto | Ação esperada | Responsável |
|---|---|---|---|
| Pagamento não confirmado | | | |
| Produto sem estoque | | | |
| Endereço inválido | | | |
| Entregador indisponível | | | |
| Falha em API externa | | | |
| Falha de permissão | | | |

---

## 9. Dados sensíveis e LGPD

Avalie se o projeto manipula informações sensíveis ou pessoais.

```md
- Dados pessoais:
- Endereços:
- Telefones:
- E-mails:
- Documentos:
- Dados financeiros:
- Informações internas:
```

**Cuidados necessários:**

```md
- 
- 
- 
```

---

## 10. Critérios de aceite

Defina como validar que as regras foram implementadas corretamente.

```md
- [ ] A regra principal foi testada.
- [ ] As exceções foram consideradas.
- [ ] Os perfis de permissão foram validados.
- [ ] Os status do processo foram testados.
- [ ] Os casos de erro têm tratamento definido.
- [ ] A operação sabe como agir em cada cenário.
```

---

## 11. Pendências

```md
- [ ] 
- [ ] 
- [ ] 
- [ ] 
```

---

## 12. Resumo das decisões

Use este espaço para registrar as principais decisões tomadas.

```md
- Decisão 1:
- Decisão 2:
- Decisão 3:
```

---

## Observações finais

```md
Adicione aqui qualquer contexto adicional, restrição, dúvida ou ponto que precise de validação futura.
```
