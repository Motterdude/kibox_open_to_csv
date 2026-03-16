# kibox_open_to_csv

Repositorio dedicado ao wrapper que converte arquivos `.open` do KiBox para `.csv` usando o `OpenToCSV.exe` instalado com o KiBox Cockpit.

## O que esta aqui

- `kibox_open_to_csv.py`: CLI + GUI para converter um arquivo ou um lote de arquivos `.open`.
- `CHANGELOG.md`: historico de construcao e separacao do repositorio.
- `HANDOFF.md`: contexto tecnico, riscos e proximos passos.

## Requisitos

- Windows com `OpenToCSV.exe` instalado a partir do pacote Kistler.
- Python 3.10+.
- O script usa apenas biblioteca padrao do Python.

## Como usar

Converter um arquivo unico:

```powershell
python .\kibox_open_to_csv.py "C:\dados\ensaio.open" --type res --separator tab --name-mode pipeline
```

Converter um diretorio de `.open` recursivamente:

```powershell
python .\kibox_open_to_csv.py "C:\dados\kibox" --output-dir "C:\dados\csv"
```

Abrir a GUI:

```powershell
python .\kibox_open_to_csv.py --gui
```

## Nome dos arquivos

O wrapper suporta tres modos:

- `source`: mantem o stem original do `.open`.
- `pipeline`: gera `*_i.csv`, util para casar com o fluxo historico das pipelines NANUM.
- `tool`: preserva o sufixo do tipo exportado, como `_res.csv`.

## Configuracao local

- O caminho escolhido para `OpenToCSV.exe` fica salvo em:
  - `%LOCALAPPDATA%\kibox_open_to_csv\kibox_open_to_csv_settings.json`
- A GUI reutiliza esse caminho nas proximas execucoes.

## Relacao com outros repositorios

- `Processamentos` mantem uma copia operacional do wrapper para uso direto com o pipeline.
- `Knock_Distribution` tambem pode manter uma copia em `tools/` para nao quebrar o fluxo do histograma.
- A manutencao canonica do conversor passa a ser feita neste repositorio.
