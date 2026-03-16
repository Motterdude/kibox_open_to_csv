# Handoff

## Objetivo entregue

Foi separado um repositorio dedicado para o conversor `.open -> .csv` do KiBox, sem arrastar junto a pipeline principal nem o modulo de histogramas de Knock.

## Conteudo publicado

- `kibox_open_to_csv.py` com:
  - execucao por CLI;
  - interface grafica em Tkinter;
  - suporte a arquivo unico ou diretorio recursivo;
  - modos de nome `source`, `pipeline` e `tool`;
  - persistencia do caminho do `OpenToCSV.exe`.
- `README.md` com uso minimo.
- `CHANGELOG.md` com a linha do tempo de extracao.

## Decisoes

- O repo ficou propositalmente simples e sem dependencia externa de Python.
- O `OpenToCSV.exe` continua sendo dependencia externa obrigatoria.
- Cada PC que for executar o wrapper precisa ter esse executavel instalado ou acessivel localmente; o repo nao redistribui o binario da Kistler.
- O caminho salvo da GUI passou a ficar em `%LOCALAPPDATA%\kibox_open_to_csv\kibox_open_to_csv_settings.json`, para nao ficar atrelado ao nome do pipeline.

## Riscos e gaps

- Sem o `OpenToCSV.exe` da Kistler, o wrapper nao funciona.
- Ter o script no Git nao elimina a necessidade da instalacao local do executavel em cada maquina de uso.
- Nao foi incluida suite automatizada de testes.
- Ainda existe copia espelhada do wrapper em outros repositorios do workspace; a expectativa daqui para frente e manter este repo como fonte principal.

## Proximo passo recomendado

- Se quiser reduzir duplicacao entre repositorios, transformar este wrapper em pacote instalavel e fazer os outros repositorios consumirem a mesma origem.
