# RulingBR
This dataset contains decisions from Supremo Tribunal Federal in Portuguese.
These decisions were downloaded and parsed from https://www.stf.jus.br/. They are from the years 2011 to 2018.

## Using
Extract:

```bash
!tar xJvf rulingbr-v1.2.tar.xz
```

Load (Python):

```python
docs = []
with open('rulingbr-v1.2.jsonl') as f:
  for line in f:
    obj = json.loads(line)
    docs.append(obj)

obj = docs[0]
print('{}: {}'.format(obj['relator'], obj['ementa'][:52]))
```
    
## Structure
For ease parsing of the file, each line contains a complete JSON object divided into 4 sections: "ementa", "acordao", "relatorio", "voto", "area", "relator", "classe", "extrato".

### Ementa
Ground-truth summary from another sections.

### Relatorio
General description about the case. 

### Voto
Judge vote(s). It contains one or more votes from the judges. This document presents the critical aspects considered for the decision.

### Acordao
This is the final decision. It is the compilation of the votes.

### Area
Broad topic about the decision. Main areas:

- direito administrativo
- direito ambiental
- direito civil
- direito constitucional
- direito do consumidor
- direito econômico
- direito eleitoral
- direito financeiro
- direito internacional público
- direito processual civil
- direito processual penal
- direito penal
- direito previdenciário
- direito do trabalho
- direito notarial
- direito tributário
- direito urbanístico

### Classe
It is the specific juridic instrument. It can be one of the following. They may also be combined. 

#### Incidentais
- ação cautelar
- ação cautelar incidental
- agravo de instrumento
- agravo regimental
- embargos de declaração
- embargos de divergência
- embargos infringentes
- questão de ordem

#### Ações Autônomas
- ação direta de inconstitucionalidade
- ação declaratória de constitucionalidade
- ação civil pública
- ação ordinária
- arguição de descumprimento de preceito fundamental
- ação penal
- ação popular
- ação rescisória
- conflito de competência
- ação rescisória
- denúncia
- inquérito
- mandado de injunção
- mandado de segurança
- pedido de intervenção
- reclamação
- recurso extraordinário
- habeas corpus
- queixa-crime
- pedido de extradição

 #### Recursos
- recurso ordinário
- recurso de agravo
- recurso em sentido estrito

### Relator
The name of the judge responsible for composing the report and the first vote of the decision. 

- alexandre de moraes
- ayres britto
- carmen lucia
- celso de mello
- cezar peluso
- dias toffoli
- edson fachin
- ellen gracie
- eros grau
- gilmar mendes
- joaquim barbosa
- luiz fux
- marco aurélio
- ricardo lewandowski
- roberto barroso
- rosa weber
- sepúlveda pertence
- teori zavascki


## Extrato
Additional information. This section is missing in near 50% of the cases.

## Versions
- 1.0 - Original work presented at PROPOR 2018 Conference
- 1.1 - Manual corrections on ementa section. Split test/train/validation
- 1.2 - Deduplication with removal of 49 near identical samples. Created new sections "relator", "classe", "area", "extrato". It can now be used for categorization tasks.

## Citation

```bibtex
@inproceedings{feijo2018rulingbr,
    title={Rulingbr: A summarization dataset for legal texts},
    author={de Vargas Feij{\'o}, Diego and Moreira, Viviane Pereira},
    booktitle={International Conference on Computational Processing of the Portuguese Language},
    pages={255--264},
    year={2018},
    organization={Springer},
    url={https://link.springer.com/chapter/10.1007/978-3-319-99722-3_26}
}
```
