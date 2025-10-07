# 🚀 Como Usar o Tradutor

## 📋 Início Rápido

### Google Colab (Recomendado)

1. Acesse [Google Colab](https://colab.research.google.com)
2. Faça upload do arquivo `tradutor_artigos_azure.py`
3. Cole todo o código em uma célula
4. Configure suas credenciais Azure
5. Execute com `Shift + Enter`

### Python Local

```bash
# Clone o repositório
git clone https://github.com/Agathx/tradutor-artigos-azure-ai.git
cd tradutor-artigos-azure-ai

# Instale dependências
pip install -r requirements.txt

# Execute
python tradutor_artigos_azure.py
```

---

## 🎯 Modos de Operação

### Modo 1: Tradução Direta

**Quando usar:** Textos curtos, testes rápidos, traduções simples

**Como usar:**
```
1. Execute o programa
2. Digite: 1
3. Cole seu texto
4. Escolha idioma de destino (ex: pt, en, es)
5. Receba a tradução instantaneamente
```

**Exemplo:**
```
Digite: 1

Cole o texto:
> Machine learning is revolutionizing technology

Idioma de destino: pt

Resultado:
> O aprendizado de máquina está revolucionando a tecnologia
```

---

### Modo 2: Upload de Arquivo

**Quando usar:** Artigos longos, PDFs, documentos completos

**Como usar:**
```
1. Execute o programa
2. Digite: 2
3. Faça upload do arquivo (.txt ou .pdf)
4. Aguarde processamento
5. Escolha idioma de destino
6. Baixe o resultado
```

**Formatos suportados:**
- ✅ `.txt` - Arquivos de texto simples
- ✅ `.pdf` - Documentos PDF (apenas texto extraível)

**Exemplo:**
```
Digite: 2

[Faça upload de: artigo_ia.pdf]

📄 Arquivo: artigo_ia.pdf
✅ 15.234 caracteres extraídos
🔍 Idioma detectado: EN

Idioma de destino: pt

🌐 Traduzindo... ████████████ 100%

✅ Tradução completa!
💾 Arquivo salvo: traducao_resultado.txt
```

---

### Modo 3: Opções Avançadas

**Quando usar:** Análise detalhada, estudos linguísticos, pesquisa

**Como usar:**
```
1. Execute o programa
2. Digite: 3
3. Cole o texto
4. Configure opções avançadas:
   - Alinhamento de palavras
   - Comprimento de frases
   - Filtro de conteúdo
5. Receba análise completa
```

**Exemplo:**
```
Digite: 3

Texto: Smart Services

Idioma destino: zh-Hans

Incluir alinhamento? s
Incluir comprimento? s
Filtro ofensivo? n

Resultado:
> 智能服务

Alinhamento:
> 0:5-0:4 6:13-6:13
> (Smart→智能 Services→服务)

Comprimento:
> Fonte: 14 caracteres
> Destino: 4 caracteres
```

---

## 💡 Casos de Uso Práticos

### 1. Traduzir Artigo Técnico

**Cenário:** Você encontrou um paper científico em inglês

```bash
Passo 1: Baixe o PDF do artigo
Passo 2: Execute o tradutor (modo 2)
Passo 3: Upload do PDF
Passo 4: Escolha: pt
Passo 5: Leia o resultado em português
```

**Tempo estimado:** 30 segundos para artigo de 10 páginas

---

### 2. Comparar Traduções

**Cenário:** Testar qualidade da tradução em vários idiomas

```bash
# Teste 1: EN → PT
Modo 1 > Cole texto > Destino: pt

# Teste 2: EN → ES
Modo 1 > Cole texto > Destino: es

# Teste 3: EN → FR
Modo 1 > Cole texto > Destino: fr

Compare os resultados!
```

---

### 3. Análise Linguística

**Cenário:** Estudar como palavras correspondem entre idiomas

```bash
Modo 3 > Texto técnico
> Ativar alinhamento: SIM
> Ver mapeamento palavra por palavra
```

**Útil para:**
- Estudantes de linguística
- Tradutores profissionais
- Pesquisadores de NLP

---

## ⚙️ Configurações Opcionais

### Alterar Idioma Padrão

No código, modifique:
```python
idioma_destino = input("Idioma de destino: ").strip() or 'pt'
#                                                          ↑
# Altere 'pt' para seu idioma preferido
```

### Aumentar Tamanho de Chunk

Para textos muito longos:
```python
max_chunk_size = 10000  # Padrão
# Aumente para 20000 se necessário
```

### Adicionar Delay (Rate Limiting)

Para evitar erros de quota:
```python
import time

def traduzir_com_delay(texto, ...):
    resultado = tradutor.traduzir(texto, ...)
    time.sleep(1)  # Aguarda 1 segundo
    return resultado
```

---

## 🎨 Idiomas Suportados

### Principais Idiomas

| Código | Idioma | Exemplo |
|--------|--------|---------|
| `pt` | Português | Olá mundo |
| `en` | Inglês | Hello world |
| `es` | Espanhol | Hola mundo |
| `fr` | Francês | Bonjour monde |
| `de` | Alemão | Hallo Welt |
| `it` | Italiano | Ciao mondo |
| `ja` | Japonês | こんにちは世界 |
| `zh-Hans` | Chinês (Simpl.) | 你好世界 |
| `ko` | Coreano | 안녕하세요 세계 |
| `ru` | Russo | Привет мир |

[Lista completa de 100+ idiomas](https://docs.microsoft.com/azure/cognitive-services/translator/language-support)

---

## 📊 Limites e Performance

### Plano Gratuito (F0)

```yaml
Limites:
  Caracteres/mês: 2.000.000
  Caracteres/requisição: 50.000
  Requisições/minuto: ~10-20 (variável)
  
Performance:
  Latência média: 0.5-2 segundos
  Textos curtos (<1k): <1 segundo
  Textos longos (>10k): 3-10 segundos
```

### Estimativas

| Tipo de Conteúdo | Caracteres | Tempo Estimado |
|------------------|------------|----------------|
| Tweet | 280 | < 1s |
| Email | 1.000 | 1s |
| Artigo blog | 5.000 | 2-3s |
| Paper científico | 30.000 | 10-15s |
| Livro capítulo | 50.000 | 20-30s |

---

## 🔧 Troubleshooting

### "Erro na tradução"

**Possíveis causas:**
1. Chave Azure inválida
2. Quota excedida
3. Texto muito longo

**Solução:**
```python
# Verifique:
print(AzureTranslatorConfig.SUBSCRIPTION_KEY)  # Está correta?
print(len(texto))  # Menor que 50.000?
```

### "Idioma não detectado"

**Solução:** Especifique manualmente
```python
tradutor.traduzir(texto, 
                  idioma_destino='pt',
                  idioma_origem='en')  # ← Especifique aqui
```

### PDF não extrai texto

**Causa:** PDF com imagens/OCR necessário

**Solução:**
1. Use ferramenta de OCR primeiro
2. Ou copie/cole texto manualmente

---

## 💾 Salvando Resultados

### Formato Padrão (.txt)

Automático ao escolher salvar:
```
traducao_resultado.txt
```

### Formato Personalizado

Modifique a função `salvar_resultado()`:
```python
# Para CSV
with open('resultado.csv', 'w') as f:
    f.write(f"Original,Traduzido\n")
    f.write(f"{texto},{traducao}\n")

# Para JSON
import json
with open('resultado.json', 'w') as f:
    json.dump({
        'original': texto,
        'traducao': traducao,
        'idioma_origem': 'en',
        'idioma_destino': 'pt'
    }, f, indent=2)
```

---

## 🎓 Dicas Avançadas

### 1. Tradução em Lote

Para múltiplos textos:
```python
textos = [
    "Hello world",
    "Good morning",
    "How are you?"
]

for texto in textos:
    resultado = tradutor.traduzir(texto, 'pt')
    print(f"{texto} → {resultado['text']}")
```

### 2. Cache de Traduções

Evite traduzir o mesmo texto 2x:
```python
cache = {}

def traduzir_com_cache(texto, idioma):
    key = f"{texto}_{idioma}"
    if key not in cache:
        cache[key] = tradutor.traduzir(texto, idioma)
    return cache[key]
```

### 3. Progress Bar

Para textos longos:
```python
from tqdm import tqdm

for chunk in tqdm(chunks, desc="Traduzindo"):
    resultado = tradutor.traduzir(chunk, 'pt')
```

---

## ✅ Checklist de Uso

```
[ ] Azure configurado
[ ] Código executando sem erros
[ ] Teste com texto simples funcionou
[ ] Upload de arquivo testado (se necessário)
[ ] Resultado salvo corretamente
[ ] Performance satisfatória
```

---

## 📚 Próximos Passos

- Ver [Exemplos Práticos](exemplos.md)
- Voltar para [Configuração Azure](configuracao-azure.md)
- Consultar [README Principal](../README.md)

---

**Dúvidas?** Abra uma [Issue no GitHub](https://github.com/Agathx/tradutor-artigos-azure-ai/issues)
