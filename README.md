# Validação de Templates de Pull Request

Este repositório contém uma GitHub Action que valida automaticamente os templates de Pull Request, garantindo que todos os campos obrigatórios sejam preenchidos corretamente.

## 🎯 Funcionalidades

- **Detecção automática** do tipo de template (Feature ou Bug)
- **Validação de campos obrigatórios** específicos para cada tipo
- **Rejeição de valores padrão** (lorem ipsum, MK-XXXX, etc.)
- **Campos opcionais** permitidos vazios (Observações e Demandas relacionadas)

## 📋 Templates Suportados

### Template de Feature
- ✅ Título da demanda
- ✅ Devs responsáveis
- ✅ Link da demanda
- ✅ Visão Geral
- ✅ Mudanças Implementadas
- ✅ Evidências de testes local
- ⚪ Observações (opcional)
- ⚪ Demandas relacionadas (opcional)

### Template de Bug
- ✅ Título da demanda
- ✅ Devs responsáveis
- ✅ Link da demanda
- ✅ Resumo do incidente
- ✅ Causa Raiz
- ✅ Correção Realizada
- ✅ Evidências de testes local
- ⚪ Observações (opcional)
- ⚪ Demandas relacionadas (opcional)

## 🚀 Como Funciona

A action é executada automaticamente quando:
- Um novo PR é criado
- Um PR existente é editado
- Novos commits são adicionados ao PR

### Processo de Validação

1. **Detecção do Template**: A action identifica automaticamente se é um template de feature ou bug
2. **Verificação de Campos**: Valida se todos os campos obrigatórios estão presentes
3. **Análise de Conteúdo**: Verifica se os campos têm conteúdo real (não valores padrão)

### Valores Rejeitados

A action rejeita automaticamente os seguintes valores padrão:
- `lorem ipsum dolor sit amet consectetur adipisicing elit`
- `lorem ipsum dolor sit amet`
- `lorem ipsum`
- `MK-XXXX`
- `MK-0000`

## 📁 Estrutura do Projeto

```
.github/
├── workflows/
│   └── pr-template-validation.yml    # Action principal
├── pull_request_templates/
│   ├── feature_template.md           # Template para features
│   └── bug_template.md              # Template para bugs
└── pull_request_template.md         # Template padrão
```

## 🔧 Configuração

A action está configurada para rodar em:
- **Trigger**: `pull_request` (opened, edited, synchronize)
- **Runtime**: Ubuntu latest
- **Node.js**: Versão 18

## 📝 Exemplo de Uso

1. Crie um novo Pull Request
2. Selecione um dos templates disponíveis
3. Preencha todos os campos obrigatórios com informações reais
4. A action validará automaticamente e comentará no PR
