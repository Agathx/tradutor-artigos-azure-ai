# ⚙️ Configuração do Azure

## 📋 Pré-requisitos

- Conta Microsoft (gratuita)
- Cartão de crédito para verificação (não será cobrado no plano gratuito)

---

## 🚀 Passo a Passo Completo

### 1️⃣ Criar Conta no Azure

1. Acesse [portal.azure.com](https://portal.azure.com)
2. Clique em **"Criar conta gratuita"**
3. Faça login com sua conta Microsoft
4. Complete o cadastro:
   - Informações pessoais
   - Verificação por SMS
   - Verificação de cartão (sem cobrança)

**Créditos gratuitos:** $200 USD por 30 dias + 12 meses de serviços gratuitos

---

### 2️⃣ Criar Recurso "Translator"

#### No Portal do Azure:

1. **Buscar o serviço:**
   - No menu lateral, clique em **"Criar um recurso"**
   - Na barra de busca, digite: **"Translator"**
   - Selecione **"Tradutor"** ou **"Translator"**

2. **Configurar o recurso:**

```yaml
Detalhes do Projeto:
  Assinatura: Azure subscription 1
  Grupo de recursos: rg-tradutor-artigos-tecnicos-prod
    (Clique em "Criar novo" se não existir)

Detalhes da Instância:
  Região: Brazil South
    (Escolha a região mais próxima para menor latência)
  
  Nome: tradutor-artigos-tecnicos-brs
    (Deve ser único globalmente)
  
  Camada de preços: F0 (Gratuito)
    - 2 milhões de caracteres/mês
    - Perfeito para desenvolvimento e testes
```

3. **Revisar e Criar:**
   - Clique em **"Examinar + criar"**
   - Revise as configurações
   - Clique em **"Criar"**
   - Aguarde 1-2 minutos para implantação

---

### 3️⃣ Obter Credenciais

#### Após a implantação:

1. Clique em **"Ir para o recurso"**

2. No menu lateral esquerdo, procure:
   - **"Chaves e Ponto de Extremidade"**
   - Ou **"Keys and Endpoint"** (se em inglês)

3. **Copie as seguintes informações:**

```
CHAVE 1 (KEY 1):
[sequência longa de caracteres alfanuméricos]

CHAVE 2 (KEY 2):
[outra sequência - backup da chave 1]

LOCALIZAÇÃO/REGIÃO:
brazilsouth

PONTO DE EXTREMIDADE:
https://api.cognitive.microsofttranslator.com/
```

**⚠️ IMPORTANTE:**
- Guarde a CHAVE em local seguro
- Não compartilhe publicamente
- Você pode usar CHAVE 1 ou CHAVE 2 (ambas funcionam)

---

### 4️⃣ Configurar no Código

Cole suas credenciais no código:

```python
class AzureTranslatorConfig:
    SUBSCRIPTION_KEY = "COLE_SUA_CHAVE_1_AQUI"
    ENDPOINT = "https://api.cognitive.microsofttranslator.com"
    LOCATION = "brazilsouth"  # Ou sua região
    API_VERSION = "3.0"
```

---

## 📊 Planos Disponíveis

### Plano Gratuito (F0)
```
✅ Custo: $0 USD/mês
✅ Caracteres: 2.000.000/mês
✅ Requisições: Limitadas por minuto
❌ SLA: Não garantido
```
**Ideal para:** Desenvolvimento, testes, projetos pessoais

### Plano Standard (S1)
```
💰 Custo: ~$10 USD por 1M caracteres
✅ Caracteres: Ilimitado (pay-as-you-go)
✅ Requisições: Sem limite
✅ SLA: 99.9% uptime
```
**Ideal para:** Produção, aplicações comerciais

---

## 🔐 Boas Práticas de Segurança

### ✅ Faça:
- Use variáveis de ambiente para credenciais
- Regenere chaves periodicamente
- Use diferentes recursos para dev/prod
- Monitore uso na aba "Métricas"

### ❌ Não faça:
- Commitar chaves no GitHub
- Compartilhar chaves publicamente
- Usar mesma chave em múltiplos projetos críticos
- Deixar recursos não utilizados ativos

---

## 📈 Monitoramento de Uso

### No Portal do Azure:

1. Acesse seu recurso Translator
2. Menu lateral: **"Métricas"**
3. Visualize:
   - Total de caracteres traduzidos
   - Número de requisições
   - Latência média
   - Erros

### Configurar Alertas:

```
1. Menu: "Alertas"
2. "Nova regra de alerta"
3. Configure:
   - Métrica: "Caracteres traduzidos"
   - Condição: "Maior que 1.800.000"
   - Ação: Enviar email
```

---

## 🆘 Troubleshooting

### Erro: "Access Denied"
**Solução:** Verifique se a chave está correta e não expirou

### Erro: "Quota Exceeded"
**Solução:** Você atingiu o limite mensal. Aguarde próximo mês ou upgrade para S1

### Erro: "Invalid Location"
**Solução:** Certifique-se que LOCATION está correto (ex: "brazilsouth")

### Erro: "Too Many Requests"
**Solução:** Plano gratuito tem limite de requisições/minuto. Adicione delay entre requisições

---

## 📚 Recursos Adicionais

- [Documentação Oficial](https://docs.microsoft.com/azure/cognitive-services/translator/)
- [Pricing Calculator](https://azure.microsoft.com/pricing/calculator/)
- [Status do Azure](https://status.azure.com/)
- [Suporte Azure](https://azure.microsoft.com/support/)

---

## ✅ Checklist de Configuração

```
[ ] Conta Azure criada
[ ] Recurso Translator criado
[ ] CHAVE 1 copiada
[ ] LOCALIZAÇÃO identificada
[ ] Credenciais configuradas no código
[ ] Teste básico realizado
[ ] Monitoramento configurado (opcional)
```

---

**Próximo passo:** [Como Usar o Sistema](como-usar.md)
