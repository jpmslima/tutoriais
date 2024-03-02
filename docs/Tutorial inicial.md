# Tutorial inicial

### Objetivos

- Identificar sequências por meio da busca por similaridade do BLAST.
- Realizar o alinhamento múltiplo de sequências utilizando o [Jalview](jalview.org).

## Conhecendo suas sequências

Para executar uma análise filogenética, uns dos primeiros passos é encontrar um marcador adequado (uma sequência de nucleotídeos ou  aminoácidos). Em seguida, você tem construir um conjunto de dados (*dataset*) com sequências homólogas alinhadas (ou seja, um Alinhamento Múltiplo de Sequências - MSA) a ser usado no *pipeline* de filogenia subsequente.

Neste exemplo, você vai começar a partir da seqüência abaixo, usando o arquivo ```.fasta```.

A primeira coisa a fazer é identificar esta sequência usando uma busca de similaridade usando o programa BLAST. Para isso, você pode usar BLASTn ou BLASTx.

```
>HomoSapiens
AUGACCCCAAUACGCAAAAUUAACCCCCUAAUAAAAUUAAUUAACCACUCAUUCAUCGAC
CUCCCCACCCCAUCCAACAUCUCCGCAUGAUGAAACUUCGGCUCACUCCUUGGCGCCUGC
CUGAUCCUCCAAAUCACCACAGGACUAUUCCUAGCCAUACACUACUCACCAGACGCCUCA
ACCGCCUUUUCAUCAAUCGCCCACAUCACUCGAGACGUAAAUUAUGGCUGAAUCAUCCGC
UACCUUCACGCCAAUGGCGCCUCAAUAUUCUUUAUCUGCCUCUUCCUACACAUCGGGCGA
GGCCUAUAUUACGGAUCAUUUCUCUACUCAGAAACCUGAAACAUCGGCAUUAUCCUCCUG
CUUGCAACUAUAGCAACAGCCUUCAUAGGCUAUGUCCUCCCGUGAGGCCAAAUAUCAUUC
UGAGGGGCCACAGUAAUUACAAACUUACUAUCCGCCAUCCCAUACAUUGGGACAGACCUA
GUUCAAUGAAUCUGAGGAGGCUACUCAGUAGACAGUCCCACCCUCACACGAUUCUUUACC
UUUCACUUCAUCUUACCCUUCAUUAUUGCAGCCCUAGCAGCACUCCACCUCCUAUUCUUG
CACGAAACGGGAUCAAACAACCCCCUAGGAAUCACCUCCCAUUCCGAUAAAAUCACCUUC
CACCCUUACUACACAAUCAAAGACGCCCUCGGCUUACUUCUCUUCCUUCUCUCCUUAAUG
ACAUUAACACUAUUCUCACCAGACCUCCUAGGCGACCCAGACAAUUAUACCCUAGCCAAC
CCCUUAAACACCCCUCCCCACAUCAAGCCCGAAUGAUAUUUCCUAUUCGCCUACACAAUU
CUCCGAUCCGUCCCUAACAAACUAGGAGGCGUCCUUGCCCUAUUACUAUCCAUCCUCAUC
CUAGCAAUAAUCCCCAUCCUCCAUAUAUCCAAACAACAAAGCAUAAUAUUUCGCCCACUA
AGCCAAUCACUUUAUUGACUCCUAGCCGCAGACCUCCUCAUUCUAACCUGAAUCGGAGGA
CAACCAGUAAGCUACCCUUUUACCAUCAUUGGACAAGUAGCAUCCGUACUAUACUUCACA
ACAAUCCUAAUCCUAAUACCAACUAUCUCCCUAAUUGAAAACAAAAUACUCAAA
```

Muitas vezes a sequência alvo é obtida por sequenciamento de DNA (em experimentos de genoma ou transcriptoma), uma vez que estes métodos são normalmente mais acessíveis que os métodos de obtenção de sequências de aminoácidos. Para realizar a busca de similaridade a partir da sequência de nucleotídeos, você tem duas opções:

- Traduzir a sequência de nucleotídeos nos 3 *frames* e usar as sequências de aminoácidos resultantes como *input* em uma busca de similaridade com o BLASTp. A tradução pode ser realizada usando as ferramentas do [EXPASY] (https://web.expasy.org/cgi-bin/translate/dna2aa.cgi) ou do [EBI](https://www.ebi.ac.uk/ Tools/st/).
- Usar diretamente o [BLASTx] (https://blast.ncbi.nlm.nih.gov/Blast.cgi?PROGRAM=blastx&PAGE_TYPE=BlastSearch&BLAST_SPEC=&LINK_LOC=blasttab&LAST_PAGE=blastn&QUERY=AB823629.1). Esta variação do BLAST traduz a sequência de nucleotídeos de entrada (*Query*) e a compara com um banco de proteínas.

Aqui vamos usar o [BLASTx] (https://blast.ncbi.nlm.nih.gov/Blast.cgi?PROGRAM=blastx&PAGE_TYPE=BlastSearch&BLAST_SPEC=&LINK_LOC=blasttab&LAST_PAGE=blastn&QUERY=AB29).

**Passos:**

- Abra a página do [NCBI-BLAST](https://blast.ncbi.nlm.nih.gov/Blast.cgi).

![BLAST](https://drive.google.com/uc?id=1CZ0GD_Ad0QpCj34uw0F6Vv_RZdh2eEa4)

- Clique em blastx. A página abaixo irá abrir. Cole sua sequência no campo indicado e escolha o banco de dados nr (*nr database*). Depois, só clicar em ```BLAST```.

![BLASTx](https://drive.google.com/uc?id=1au3i82_mPv438f9MPmhx80AmgYONDwSg)

- Após alguns momentos, o resultado da busca irá aparecer, como o abaixo:

![BLASTx](https://drive.google.com/uc?id=1z_pYNKMou0TSJxU91ODerO1qKsnl3xul)

- Clique em alinhamentos e analise os resultados.

![BLASTx](https://drive.google.com/uc?id=1fewCtlD82mHeDIoYGY4FZZRXPgJCcXn8)

> *Você também pode traduzir a sequência nucleotídica em seu frame +1 e realizar uma busca com o BLASTp, usando a sequência de aminoácidos.

### Questões

1- Qual proteína essa sequência codifica?
2- Qual a função dessa proteína?

## Alinhamento Múltiplo de Sequências

Vamos supor que o seu objetivo é inferir uma filogenia tomando como partida a sequência acima. A partir dela e usando busca de similaridades, você irá procurar sequências homólogas de outras espécies (de diferentes *ranks* taxonômicos). Existem uma série de opções tanto na página das configurações do BLAST, como na página de resultados da busc que permitem você fazer uma seleção das sequências por espécie e por nível taxonômico. Selecionando as sequências, você pode até já exportar diretamente o arquivo multifasta para posterior alinhamento.

Por exemplo, encontramos e selecionamos as sequências abaixo:

```
>MasturusLanceolatus
AUGGCAAGCCUGCGUAAAACCCACCCACUAUUAAAAAUUGCAAACGACGCACUAGUCGAC
CUCCCCACCCCUUCAAACAUCUCCGCCUGAUGGAAUUUUGGCUCCCUACUUGGACUCUGC
CUAAUUAUCCAAAUUCUUACUGGACUAUUCCUCGCAAUACAUUACACCUCCGAUAUCGCU
ACUGCAUUCUCAUCCGUGGCACAUAUUUGCCGAGAUGUAAACUACGGCUGACUCAUCCGC
AACCUGCAUGCUAACGGAGCAUCUUUCUUCUUUAUUUGUAUUUAUAUGCACAUCGCCCGA
GGCCUAUACUAUGGCUCCUACCUCUAUAAAGAAACCUGAAACGUCGGAGUAGUCCUAUUA
CUCUUGGUCAUGGCGACCGCUUUCGUAGGCUACGUACUUCCCUGAGGACAAAUAUCUUUC
UGGGGCGCUACUGUUAUUACUAACCUCUUCUCCGCCGUCCCCUAUGUGGGCGAUGCCCUC
GUACAAUGGAUCUGAGGAGGAUUCUCAGUUGACAACGCCACAUUAACACGAUUCUUUGCC
UUCCAUUUCCUCCUCCCCUUCAUCGUUACAGCAGUCACCCUAAUCCAUUUACUAUUCCUC
CACGAAACAGGCUCAAAUAACCCCCUGGGGCUAAGUUCAAACACGGACAAAAUCUCUUUC
CACCCUUACUUCUCCUACAAAGAUCUCUUAGGCUUCACAAUCAUGCUUAUUGCCCUCACA
UCCCUAGCACUCUUCUCCCCCAACCUCCUGGGAGACCCUGACAACUUCACCCCCGCCAAC
CCCCUUGUCACCCCACCCCACAUCAAGCCCGAGUGAUACUUCCUGUUCGCUUACGCCAUU
CUUCGCUCCAUCCCAAAUAAAUUAGGAGGAGUCCUUGCCUUGCUGGCCUCCAUCCUAGUC
CUAAUAGUCGUACCGCUUCUCCACACAUCCAAACAGCGAGGCCUCACGUUCCGCCCCCUU
ACCCAAUUCCUAUUUUGAACCUUAAUUGCCAACAUUAUUAUUCUAACAUGAAUUGGAGGA
AUACCCGUAGAACACCCAUUCGUGAUCAUCGGCCAAAUCGCCUCCGUCCUUUACUUCUCC
CUAUUCCUAGUCUUCAUCCCCCUCACAGGCUGACUAGAAAACAAAGCCCUUGAAUGGUCC
>HomoSapiens
AUGACCCCAAUACGCAAAAUUAACCCCCUAAUAAAAUUAAUUAACCACUCAUUCAUCGAC
CUCCCCACCCCAUCCAACAUCUCCGCAUGAUGAAACUUCGGCUCACUCCUUGGCGCCUGC
CUGAUCCUCCAAAUCACCACAGGACUAUUCCUAGCCAUACACUACUCACCAGACGCCUCA
ACCGCCUUUUCAUCAAUCGCCCACAUCACUCGAGACGUAAAUUAUGGCUGAAUCAUCCGC
UACCUUCACGCCAAUGGCGCCUCAAUAUUCUUUAUCUGCCUCUUCCUACACAUCGGGCGA
GGCCUAUAUUACGGAUCAUUUCUCUACUCAGAAACCUGAAACAUCGGCAUUAUCCUCCUG
CUUGCAACUAUAGCAACAGCCUUCAUAGGCUAUGUCCUCCCGUGAGGCCAAAUAUCAUUC
UGAGGGGCCACAGUAAUUACAAACUUACUAUCCGCCAUCCCAUACAUUGGGACAGACCUA
GUUCAAUGAAUCUGAGGAGGCUACUCAGUAGACAGUCCCACCCUCACACGAUUCUUUACC
UUUCACUUCAUCUUACCCUUCAUUAUUGCAGCCCUAGCAGCACUCCACCUCCUAUUCUUG
CACGAAACGGGAUCAAACAACCCCCUAGGAAUCACCUCCCAUUCCGAUAAAAUCACCUUC
CACCCUUACUACACAAUCAAAGACGCCCUCGGCUUACUUCUCUUCCUUCUCUCCUUAAUG
ACAUUAACACUAUUCUCACCAGACCUCCUAGGCGACCCAGACAAUUAUACCCUAGCCAAC
CCCUUAAACACCCCUCCCCACAUCAAGCCCGAAUGAUAUUUCCUAUUCGCCUACACAAUU
CUCCGAUCCGUCCCUAACAAACUAGGAGGCGUCCUUGCCCUAUUACUAUCCAUCCUCAUC
CUAGCAAUAAUCCCCAUCCUCCAUAUAUCCAAACAACAAAGCAUAAUAUUUCGCCCACUA
AGCCAAUCACUUUAUUGACUCCUAGCCGCAGACCUCCUCAUUCUAACCUGAAUCGGAGGA
CAACCAGUAAGCUACCCUUUUACCAUCAUUGGACAAGUAGCAUCCGUACUAUACUUCACA
ACAAUCCUAAUCCUAAUACCAACUAUCUCCCUAAUUGAAAACAAAAUACUCAAA
>BosTaurus
AUGACUAACAUUCGAAAGUCCCACCCACUAAUAAAAAUUGUAAACAAUGCAUUCAUCGAC
CUUCCAGCCCCAUCAAACAUUUCAUCAUGAUGAAAUUUCGGUUCCCUCCUGGGAAUCUGC
CUAAUCCUACAAAUCCUCACAGGCCUAUUCCUAGCAAUACACUACACAUCCGACACAACA
ACAGCAUUCUCCUCUGUUACCCAUAUCUGCCGAGACGUGAACUACGGCUGAAUCAUCCGA
UACAUACACGCAAACGGAGCUUCAAUGUUUUUUAUCUGCUUAUAUAUGCACGUAGGACGA
GGCUUAUAUUACGGGUCUUACACUUUUCUAGAAACAUGAAAUAUUGGAGUAAUCCUUCUG
CUCACAGUAAUAGCCACAGCAUUUAUAGGAUACGUCCUACCAUGAGGACAAAUAUCAUUC
UGAGGAGCAACAGUCAUCACCAACCUCUUAUCAGCAAUCCCAUACAUCGGCACAAAUUUA
GUCGAAUGAAUCUGAGGCGGAUUCUCAGUAGACAAAGCAACCCUUACCCGAUUCUUCGCU
UUCCAUUUUAUCCUUCCAUUUAUCAUCAUAGCAAUUGCCAUAGUCCACCUACUAUUCCUC
CACGAAACAGGCUCCAACAACCCAACAGGAAUUUCCUCAGACGUAGACAAAAUCCCAUUC
CACCCCUACUAUACCAUUAAGGACAUCUUAGGGGCCCUCUUACUAAUUCUAGCUCUAAUA
CUACUAGUACUAUUCGCACCCGACCUCCUCGGAGACCCAGAUAACUACACCCCAGCCAAU
CCACUCAACACACCCCCUCACAUCAAACCCGAGUGAUACUUCUUAUUUGCAUACGCAAUC
UUACGAUCAAUCCCCAACAAACUAGGAGGAGUACUAGCCCUAGCCUUCUCUAUCCUAAUU
CUUGCUCUAAUCCCCCUACUACACACCUCCAAACAACGAAGCAUAAUAUUCCGACCACUC
AGCCAAUGCCUAUUCUGAGCCCUAGUAGCAGACCUACUGACACUCACAUGAAUUGGAGGA
CAACCAGUCGAACACCCAUAUAUCACCAUCGGACAACUAGCAUCUGUCCUAUACUUUCUC
CUCAUCCUAGUGCUAAUACCAACGGCCGGCACAAUCGAAAACAAAUUACUAAAAUGA
>BalaenopteraMusculus
AUGACCAACAUCCGAAAAACACACCCACUAAUAAAAAUCAUCAACGAUGCAUUCAUUGAU
CUCCCUACCCCAUCAAACAUCUCCUCAUGAUGAAACUUCGGCUCCCUACUCGGCCUCUGC
UUAAUUGUACAAAUCCUAACAGGCCUAUUCCUAGCAAUACACUAUACACCAGACACAAUA
ACCGCCUUCUCAUCAGUCACACAUAUUUGCCGAGACGUAAACUAUGGCUGAGUUAUUCGG
UACUUACAUGCAAACGGAGCCUCCAUAUUCUUCAUCUGCCUCUACGCCCACAUGGGACGA
GGUCUAUACUACGGCUCCCACGCUUUUCGAGAAACAUGAAAUAUUGGAGUUAUUCUACUA
UUCACGGUCAUAGCCACUGCAUUCGUAGGCUACGUCCUGCCCUGAGGACAAAUAUCAUUC
UGAGGCGCAACCGUCAUCACCAACCUCCUAUCAGCAAUCCCAUACAUUGGUACUACCCUA
GUCGAAUGAAUCUGAGGCGGUUUUUCUGUGGAUAAAGCAACACUAACACGCUUCUUUGCC
UUCCACUUCAUUCUCCCCUUCAUCAUUAUAGCAUUAGCAAUCGUCCACCUCAUCUUCCUU
CACGAAACAGGAUCCAACAACCCCACAGGUAUCCCAUCUGACAUAGAUAAAAUUCCAUUC
CACCCCUACUACACAAUUAAAGACAUUCUAGGCGCCCUACUACUAAUCCUAACCCUACUA
AUAUUAACUCUAUUUGCACCCGACUUACUCGGAGACCCAGACAACUACACCCCAGCAAAC
CCACUCAGUACCCCAGCACACAUUAAACCAGAGUGAUAUUUCCUAUUUGCAUAUGCAAUC
CUACGAUCAAUCCCCAACAAAUUAGGCGGAGUCUUAGCCCUACUACUCUCAAUCCUAGUC
CUAGCUCUAAUCCCAAUACUCCACACAUCCAAACAACGAAGCAUAAUAUUCCGACCCUUU
AGCCAAUUCCUGUUUUGAGUACUGGUCGCAGACCUACUCACCCUAACGUGGAUCGGCGGC
CAACCCGUAGAACACCCCUAUGUAAUUGUAGGCCAACUCGCAUCCAUCCUCUACUUCCUC
UUAAUUCUAGUGUUAAUACCAGUAACUAGUCUUAUCGAAAAUAAACUUAUAAAAUGA
>PongoPygmaeus
AUGACCCCAAUACGCAAAACCAACCCACUAAUAAAAUUAAUUAACCACUCACUCAUCGAC
CUCCCCACCCCAUCAAACAUCUCUGCAUGAUGGAACUUCGGCUCACUUCUAGGCGCCUGC
UUAAUCAUCCAAACCAUCACUGGACUAUUCCUAGCCAUACAUUACUCACCAGACGCCACU
ACCGCCUUUUCAUCAAUCGCCCAUAUUACUCGAGAUGUAAACUACGGCUGAAUAAUCCGC
CACCUUCACGCUAACGGCGCCUCAAUGCUCUUUAUCUGCCUCUUCCUACACAUUGGCCGA
GGCUUAUACUAUGGCUCAUUCACCCACUUAGAAACCUGAAACAUUGGUAUUAUCCUACUG
UUUAUAACCAUAAUAACAGCCUUCAUAGGCUACGUCCUCCCAUGAGGCCAAAUAUCCUUC
UGAGGAGCCACAGUAAUUACAAACCUAUUAUCCGCCGUCCCAUACAUUGGAACAGACCUA
GUCCAAUGGGUCUGAGGGGGCUACUCAGUAAAUAGCCCCACUCUAACACGAUUCUUUACC
CUUCACUUCAUACUACCUUUCAUCAUUACAGCUCUAACAACCCUUCACCUCCUAUUCCUU
CACGAAACAGGAUCAAAUAACCCCCUGGGAAUCCCCUCCCACUCCGAUAAAAUCACUUUC
CACCCCUACUAUACAAUUAAAGACAUCCUAGGCCUACUCCUUUUUCUCCUCGCCCUAAUA
ACAUUAACACUACUCUCACCAGACCUCCUAAGCGACCCAGACAACUACACCUUAGCUAAC
CCCCUAAGCACCCCACCCCACAUUAAGCCCGAAUGAUACUUCCUAUUCGCCUACGCAAUC
CUACGAUCCGUCCCCAACAAACUAGGAGGUGUAAUAGCCCUCAUGCUAUCUAUCCUAAUC
CUAACAACAAUCCCCGCUCUCCACACAUCCAAGCAACAGAGCAUAACAUUCCGCCCAUUA
AGCCAAUUCCUAUACUGACUCUUAAUCACCGACCUCCUAGUUCUCACCUGAAUUGGAGGA
CAACCAGUAAGCUACCCCUUUAUUACUAUUGGCCAAGUAGCAUCCGUACUAUACUUUACC
ACUAUCCUACUCCUUAUACCAACCUCUUCCCUGAUCGAAAACUACAUACUCAAAUGAACC
>PanTroglodytes
AUGACCCCGACACGCAAAAUUAACCCACUAAUAAAAUUAAUUAAUCACUCAUUUAUCGAC
CUCCCCACCCCAUCCAACAUUUCCGCAUGAUGGAACUUCGGCUCACUUCUCGGCGCCUGC
CUAAUCCUUCAAAUUACCACAGGAUUAUUCCUAGCUAUACACUACUCACCAGACGCCUCA
ACCGCCUUCUCGUCGAUCGCCCACAUCACCCGAGACGUAAACUAUGGUUGGAUCAUCCGC
UACCUCCACGCUAACGGCGCCUCAAUAUUUUUUAUCUGCCUCUUCCUACACAUCGGCCGA
GGUCUAUAUUACGGCUCAUUUCUCUACCUAGAAACCUGAAACAUUGGCAUUAUCCUCUUG
CUCACAACCAUAGCAACAGCCUUUAUGGGCUAUGUCCUCCCAUGAGGCCAAAUAUCCUUC
UGAGGAGCCACAGUAAUUACAAACCUACUGUCCGCUAUCCCAUACAUCGGAACAGACCUG
GUCCAGUGAGUCUGAGGAGGCUACUCAGUAGACAGCCCUACCCUUACACGAUUCUUCACC
UUCCACUUUAUCUUACCCUUCAUCAUCACAGCCCUAACAACACUUCAUCUCCUAUUCUUA
CACGAAACAGGAUCAAAUAACCCCCUAGGAAUCACCUCCCACUCCGACAAAAUUACCUUC
CACCCCUACUACACAAUCAAAGAUAUCCUUGGCUUAUUCCUUUUCCUCCUUAUCCUAAUG
ACAUUAACACUAUUCUCACCAGGCCUCCUAGGCGAUCCAGACAACUAUACCCUAGCUAAC
CCCCUAAACACCCCACCCCACAUUAAACCCGAGUGAUACUUUCUAUUUGCCUACACAAUC
CUCCGAUCCAUCCCCAACAAACUAGGAGGCGUCCUCGCCCUACUACUAUCUAUCCUAAUC
CUAACAGCAAUCCCUGUCCUCCACACAUCCAAACAACAAAGCAUAAUAUUUCGCCCACUA
AGCCAACUGCUUUACUGACUCCUAGCCACAGACCUCCUCAUCCUAACCUGAAUCGGAGGA
CAACCAGUAAGCUACCCCUUCAUCACCAUCGGACAAAUAGCAUCCGUAUUAUACUUCACA
ACAAUCCUAAUCCUAAUACCAAUCGCCUCUCUAAUCGAAAACAAAAUACUUGAAUGAACC
>GallusGallus
AUGGCACCCAACAUUCGAAAAUCCCACCCCCUACUAAAAAUAAUUAACAACUCCCUAAUC
GACCUCCCAGCCCCAUCCAACAUCUCUGCUUGAUGAAAUUUCGGCUCCCUAUUAGCAGUC
UGCCUCAUGACCCAAAUCCUCACCGGCCUACUACUAGCCAUGCACUACACAGCAGACACA
UCCCUAGCCUUCUCCUCCGUAGCCCACACUUGCCGGAACGUACAAUACGGCUGACUCAUC
CGGAAUCUCCACGCAAACGGCGCCUCAUUCUUCUUCAUCUGUAUCUUCCUUCACAUCGGA
CGAGGCCUAUACUACGGCUCCUACCUCUACAAGGAAACCUGAAACACAGGAGUAAUCCUC
CUCCUCACACUCAUAGCCACCGCCUUUGUGGGCUAUGUUCUCCCAUGGGGCCAAAUAUCA
UUCUGAGGGGCCACCGUUAUCACAAACCUAUUCUCAGCAAUUCCCUACAUUGGACACACC
CUAGUAGAGUGAGCCUGAGGGGGAUUCUCAGUCGACAACCCAACCCUUACCCGAUUCUUC
GCCUUACACUUCCUCCUCCCCUUUGCAAUCGCAGGUAUUACUAUCAUCCACCUCACCUUC
CUACACGAAUCAGGCUCAAACAACCCCCUAGGCAUCUCAUCCGACUCUGACAAAAUUCCA
UUUCACCCAUACUACUCCUUCAAAGACAUUCUGGGCUUAACUCUCAUACUCACCCCAUUC
CUAACACUAGCCCUAUUCUCCCCCAACCUCCUAGGAGACCCAGAAAACUUCACCCCAGCA
AACCCACUAGUAACCCCCCCACAUAUCAAACCAGAAUGAUAUUUUCUAUUCGCCUAUGCC
AUCCUACGCUCCAUCCCCAACAAACUUGGAGGUGUACUAGCCCUAGCAGCCUCAGUCCUC
AUCCUCUUCCUAAUCCCCUUCCUCCACAAAUCUAAACAACGAACAAUAACCUUCCGACCA
CUCUCCCAAACCUUAUUCUGACUUCUAGUAGCCAACCUUCUUAUCCUAACCUGAAUCGGA
AGCCAACCAGUAGAACACCCCUUCAUCAUCAUUGGCCAAAUAGCAUCCCUCUCUUACUUC
ACCAUCCUACUUAUCCUCUUCCCCACAAUCGGAACACUAGAAAACAAAAUACUCAACUAC
>AlligatorMississippiensis
AUGACCCACCAACUACGAAAAUCCCACCCAAUCAUUAAACUCAUCAACCGCUCCCUAAUU
GACCUACCAACACCCUCAAACAUCUCCGCUUGAUGAAACUUUGGAUCACUACUAGGCCUA
ACCCUAUUAAUUCAGAUUCUAACAGGAUUCUUCUUAAUAAUGCACUUUUCAUCAAGCGAU
ACUCUAGCAUUUUCAUCUGUAUCCUACACCUCCCGCGAAGUCUGAUUUGGAUGACUCAUC
CGCAACCUCCACACAAAUGGGGCCUCCCUGUUCUUUAUAUUUAUCUUUCUUCACAUCGGA
CGAGGCCUAUACUACACAUCAUAUCUUCACGAAAGCACAUGAAAUAUUGGAGUAAUCAUA
CUUCUACUCCUAAUAGCCACAGCAUUUAUAGGCUAUGUUCUCCCAUGAGGACAAAUAUCA
UUCUGAGGAGCAACCGUAAUCACGAAUCUACUUUCUGCCACACCCUACGUUGGAAGCACU
GUCGUGCCAUGAAUUUGAGGCGGCCCCUCUGUUGACAACGCAACACUUACACGCUUCACU
GCCCUACACUUCCUCCUUCCAUUCGCCCUAUUGGCUUCACUCAUCACCCACCUGAUCUUC
CUCCAUGAACGAGGAUCAUUUAACCCCCUAGGAAUUAGCCCAAAUGCUGACAAAAUCCCA
UUCCACCCCUACUUCACCAUAAAAGACGCCCUAGGAGCAGCACUAGCUGCCUCCUCACUA
CUCAUCUUAGCUCUCUACCUACCAGCCCUAUUAGGGGACCCUGAAAACUUCACCCCAGCA
AAUUCCAUAAUUACCCCAACACACAUCAAACCCGAAUGGUACUUCCUAUUUGCUUAUGCC
AUUCUACGAUCUAUUCCAAAUAAGUUAGGAGGAGUACUAGCAAUAUUCUCAUCCAUUUUA
GUCCUAUUCCUAAUACCCGCCCUACACACAGCAAAACAACAACCAAUAUCAAUACGCCCU
AUAUCUCAGCUUCUAUUUUGAGCCCUUACCCUGGACUUCCUCUUACUCACAUGAAUCGGA
GGCCAACCAGUAAACCCCCCAUAUAUUUUAAUUGGCCAAACUGCCUCCCUAUUCUACUUC
AUCAUCAUCCUAAUCCUCAUACCAAUAGCAGGCCUCUUAGAGAACAAAAUAGUUGAACCC
ACCUAUGUUACCCCUAAG
```

Você pode baixar este arquivo multifasta [AQUI](https://drive.google.com/uc?export=download&id=1JhtIvER8uxZFrd0obkM_rbMecyEjm6Hc).

O próximo passo a se fazer é alinhar essas sequências, com o objetivo de identificar as homologias posicionais e assim poder inferir um filogenia. As sequências acima apresentam uma alta similaridade e portanto não são difíceis de se alinhar. Você pode usar qualquer programa de alinhamento nesse caso. Aqui iremos usar o programa 
[Jalview](http://www.jalview.org/).

**Passos**

- Abra o programa Jalview e feche todas as janelas de exemplo.
- A o arquivo multifasta acima, seguindo o menu mostrado na figura abaixo:
- 
![Jalview](https://drive.google.com/uc?id=1IEaubZlhl6s0cQpJR1uAFxsGO4zw2zRi)

- Em seguida, vamos colocar cores neste alinhamento usando as seguintes opções (a visualização em cores facilita a identificação de sítios semelhantes):

![Jalview](https://drive.google.com/uc?id=1_0U_iLyKqx2TFMkfz5WwAMue8YBCfGWU)

- Após isso, você pode iniciar o processo de alinhamento, usando o Clustal, como demonstrado na figura abaixo:

![Jalview](https://drive.google.com/uc?id=18Hlz0XOhP1s029UPhPW20LNrQiqAx4iI)

- O alinhamento múltiplo irá aparecer logo após a execução da tarefa. Novamente, coloque um esquema de cores para facilitar a visualização.
- Agora vamos salvar o alinhamento. Mas primeiro temos de mudar algumas opções no Jalview que dificultam a abertura dos arquivos de alinhamento exportados por outros programas. Na janela principal do Jalview, vá até o menu ```Tools``` e depois clique em preferências. A caixa de diálogo abaixo aparecerá:

![Jalview](https://drive.google.com/uc?id=1dBm8dDWdTwoUrV8uA3QZaUrGWXW2hhqT)

- Pressione a seta a direita até encontrar as opções de ```Output```. Assegure-se de que as opções são extamente as mesmas da figura abaixo. Pressione ```Ok```.
- Após isso, você pode salvar o seu alinhamento, seguindo o menu ***File > Save as...***
- Salve seu alinhamento formato fasta.