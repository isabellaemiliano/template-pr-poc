# Workflows de Validação de PR

Este repositório contém workflows do GitHub Actions para validar templates de Pull Request.

## Workflows Disponíveis

### 1. `pr-template-validation.yml` (Principal)
- **Descrição**: Workflow principal com validação completa usando Node.js
- **Funcionalidades**:
  - Detecta automaticamente o tipo de template (feature ou bug)
  - Valida campos obrigatórios
  - Rejeita valores padrão (lorem ipsum, MK-XXXX, etc.)
  - Comenta no PR com feedback detalhado

### 2. `pr-template-validation-simple.yml` (Simplificado)
- **Descrição**: Versão simplificada usando apenas bash
- **Funcionalidades**:
  - Validação básica sem dependências externas
  - Mais rápido e confiável
  - Menos complexo para debug

### 3. `pr-validation-basic.yml` (Básico - Sem Comentários)
- **Descrição**: Versão mais básica sem comentários automáticos
- **Funcionalidades**:
  - Validação essencial apenas
  - Sem dependência da API de comentários
  - Útil para testar se o problema é com comentários

### 4. `test-pr-validation.yml` (Teste)
- **Descrição**: Workflow de teste para diagnosticar problemas
- **Funcionalidades**:
  - Debug do ambiente
  - Validação básica
  - Útil para identificar problemas de execução

## Como Usar

### Para Desenvolvedores
1. Use um dos templates disponíveis em `.github/pull_request_templates/`
2. Preencha todos os campos obrigatórios com informações reais
3. Remova todos os valores padrão (lorem ipsum, MK-XXXX, etc.)
4. O workflow validará automaticamente seu PR

### Campos Obrigatórios

**Para Features:**
- Título da demanda
- Devs responsáveis
- Link da demanda
- Visão Geral
- Mudanças Implementadas
- Evidências de testes local

**Para Bugs:**
- Título da demanda
- Devs responsáveis
- Link da demanda
- Resumo do incidente
- Causa Raiz
- Correção Realizada
- Evidências de testes local

### Campos Opcionais
- Observações
- Demandas relacionadas

## Troubleshooting

### Se o workflow não executar:
1. Verifique se o PR tem um corpo preenchido
2. Confirme que está usando um template válido
3. Execute o workflow de teste para debug

### Se a validação falhar:
1. Verifique se todos os campos obrigatórios estão preenchidos
2. Remova valores padrão (lorem ipsum, MK-XXXX, etc.)
3. Preencha com informações reais sobre sua mudança

### Se aparecer erro "HttpError: Not Found":
1. Use o workflow `pr-validation-basic.yml` primeiro
2. Verifique se as permissões estão corretas
3. O problema pode ser com a API de comentários

## Estrutura dos Templates

Os templates estão localizados em:
- `.github/pull_request_templates/feature_template.md`
- `.github/pull_request_templates/bug_template.md`

## Permissões

Os workflows requerem as seguintes permissões:
- `pull-requests: read/write` - Para ler o corpo do PR e adicionar comentários
- `contents: read` - Para acessar os templates
- `issues: write` - Para adicionar comentários nos PRs

## Logs e Debug

Para debug, verifique:
1. Os logs do workflow no GitHub Actions
2. Os comentários automáticos no PR (se disponível)
3. O workflow de teste para informações detalhadas
4. Use `pr-validation-basic.yml` se houver problemas com comentários

## Ordem de Teste Recomendada

1. **Primeiro**: Teste com `pr-validation-basic.yml` (sem comentários)
2. **Segundo**: Se funcionar, teste com `pr-template-validation-simple.yml`
3. **Terceiro**: Se tudo OK, use o workflow principal
4. **Sempre**: Use `test-pr-validation.yml` para debug detalhado 