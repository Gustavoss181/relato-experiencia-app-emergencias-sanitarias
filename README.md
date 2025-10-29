# Projeto de TCC: Engenharia de Software em Cenário Crítico: Relato de Experiência na Implementação da Arquitetura Offline-First no Aplicativo Móvel UFLA-IMA para Emergências Sanitárias.

Este repositório contém o desenvolvimento do meu Trabalho de Conclusão de Curso. O documento é escrito em LaTeX (utilizando a suíte `TeX Live`) e editado no `Visual Studio Code` com a extensão [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop).

O versionamento é controlado via `Git`, seguindo um fluxo de trabalho específico para garantir a integridade do histórico e facilitar o desenvolvimento.

* **Autor:** [Seu Nome Completo]
* **Curso:** [Seu Curso]
* **Universidade:** [Nome da Universidade, ex: UFLA]
* **Orientador(a):** Prof.(a) Dr(a). [Nome do Orientador]
* **Coorientador(a):** [Nome do Coorientador, se aplicável]

![Status](https://img.shields.io/badge/status-em_desenvolvimento-yellow)

---

## 🏗️ Estrutura de Pastas (Sugestão)

Para manter o projeto organizado, a seguinte estrutura de diretórios é utilizada:

```
/
├── .gitignore           # Ignora arquivos auxiliares do LaTeX e PDFs
├── README.md            # Este arquivo
├── main.tex             # Arquivo LaTeX principal (mestre)
├── referencias.bib      # Arquivo de referências BibTeX
├── abnt-estilo.cls      # Arquivo de estilo da universidade (ex: ABNT)
|
├── 0_pretextuais/       # Pasta para capa, resumo, sumário, etc.
│   ├── resumo.tex
│   └── agradecimentos.tex
|
├── 1_textuais/          # Pasta para o conteúdo principal
│   ├── 1_introducao.tex
│   ├── 2_metodologia.tex
│   ├── 3_resultados.tex
│   └── 4_conclusao.tex
|
├── 2_postextuais/       # Pasta para referências e apêndices
│   └── apendices.tex
|
└── assets/                # Imagens, gráficos, e outros recursos
    └── fluxo_de_dados.png
```

---

## 🚀 Fluxo de Trabalho Git (Git Workflow)

Este projeto utiliza um fluxo de versionamento baseado no GitFlow, simplificado para um projeto acadêmico individual.

### 1. Branch `main` (ou `principal`)
* **Propósito:** Armazena **apenas** as versões finais, entregues e defendidas. Esta branch representa o produto "pronto".
* **Regra:** Nunca recebe commits diretos. Apenas recebe merges da `develop` em marcos de entrega muito importantes (ex: "Versão de qualificação", "Versão de defesa", "Versão final corrigida").

### 2. Branch `develop`
* **Propósito:** Branch principal de desenvolvimento. É a "fonte da verdade" do rascunho mais atual e completo do TCC.
* **Regra:** Não deve receber commits diretos. Serve como base para criar novas *branches de trabalho* e recebe merges delas quando o trabalho é concluído.

### 3. Branches de Trabalho (Temporárias)
* **Propósito:** Todo novo trabalho, seja um capítulo novo ou uma correção, é feito em uma branch separada, criada a partir da `develop`.
* **Regra:** Elas são temporárias. São criadas, recebem os commits e, ao final, são mescladas (merge) de volta na `develop` e depois apagadas.
* **Padrão de Nomenclatura:**
    * **`capitulo/nome-do-capitulo`**: Para escrever novos capítulos ou seções grandes.
        * `capitulo/introducao`
        * `capitulo/metodologia`
    * **`correcao/descricao-da-correcao`**: Para aplicar correções pedidas pelo orientador ou que foram percebidas.
        * `correcao/feedback-orientador-v1`
        * `correcao/ajuste-abnt-referencias`
    * **`refactor/ajuste-estrutura`**: Para mudanças estruturais que não são conteúdo novo.
        * `refactor/reorganiza-pastas-de-imagem`
        * `refactor/limpa-preambulo-latex`

---

## 🔄 Ciclo de Revisão com Orientadores

O orientador **não** interage com o Git. O fluxo de revisão acontece externamente, usando o PDF como artefato.

1.  **Eu (Desenvolvedor):**
    * Finalizo um conjunto de tarefas (ex: `capitulo/introducao` e `capitulo/metodologia`) e faço o merge de ambas para a `develop`.
    * **Gero um PDF** a partir da branch `develop`.
    * (Opcional, mas recomendado) Crio uma `tag` no Git para marcar esta versão:
        * `git tag -a v0.1-revisao -m "Versão 0.1 enviada para orientadores"`
    * Envio o PDF por e-mail para os orientadores (ex: `TCC_v0.1.pdf`).

2.  **Orientador(a):**
    * Recebe o PDF, faz anotações, comentários e envia o feedback de volta (seja em um PDF comentado, e-mail, etc.).

3.  **Eu (Desenvolvedor):**
    * Recebo o feedback.
    * A partir da `develop`, crio uma nova branch:
        * `git checkout -b correcao/feedback-orientador-v1`
    * Aplico **todas** as correções nessa branch, fazendo commits pequenos e descritivos.
    * Ao terminar, faço o merge da branch `correcao/` de volta na `develop`.
    * Apago a branch de correção.
    * O ciclo recomeça para a próxima rodada de revisão.

---

## ⚙️ Como Compilar o PDF

1.  Garanta que você tem uma distribuição LaTeX instalada (como `TeX Live` ou `MiKTeX`).
2.  No VSCode, tenha a extensão [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) instalada.
3.  Abra o arquivo `main.tex`.
4.  Use o comando da extensão para "Build LaTeX project" (atalho padrão: `Ctrl+Alt+B` no Windows/Linux, `Cmd+Option+B` no macOS).
5.  O PDF (`main.pdf`) será gerado na pasta raiz.
    * *Nota: O arquivo `main.pdf` é propositalmente ignorado pelo `.gitignore` para não poluir o repositório com binários.*