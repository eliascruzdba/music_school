```markdown
# Tutorial de Git e GitHub – Branch e Pull Request (Visual)

Este tutorial mostra o **fluxo completo de trabalho com Git e GitHub** usando branches, commits, push e Pull Requests, com diagramas que facilitam o entendimento.

---

## Pré-requisitos

- Git instalado: [Download Git](https://git-scm.com/downloads)  
- Conta no GitHub: [Cadastro GitHub](https://github.com/join)

---

## Cenário 1 – Criação de Projeto

Fluxo lógico da criação de um projeto no GitHub:

```

GitHub
main
│
│ clone
▼
Local
main
│
│ git checkout -b feature/music_repo01
▼
feature/music_repo01
│
│ add + commit
│ git push -u origin feature/music_repo01
▼
GitHub
feature/music_repo01
│
│ Pull Request → Merge
▼
GitHub
main (atualizado)

````

### Passos:

1. Criar repositório no GitHub: `music_school.git`
2. Clonar o repositório:
   ```bash
   git clone https://github.com/eliascruzdba/music_school.git
   cd music_school
````

3. Criar branch:

   ```bash
   git checkout -b feature/music_repo01
   ```
4. Adicionar arquivo `music_school.py`:

   ```bash
   git add music_school.py
   git commit -m "Adiciona arquivo music_school.py"
   git push -u origin feature/music_repo01
   ```
5. No GitHub, criar Pull Request e fazer Merge na `main`.

---

## Cenário 2 – Alteração de Código (PySpark Colab)

Fluxo lógico de alteração:

```
GitHub
  main
   │ clone
   ▼
Local
  main
   │
   │ git checkout -b feature/pyspark_colab
   ▼
  feature/pyspark_colab
   │
   │ add + commit
   │ git push -u origin feature/pyspark_colab
   ▼
GitHub
  feature/pyspark_colab
   │
   │ Pull Request → Merge
   ▼
GitHub
  main (atualizado)
```

### Passos:

1. Clonar repositório:

   ```bash
   git clone https://github.com/eliascruzdba/music_school.git
   cd music_school
   ```
2. Criar código PySpark (exemplo Colab):

   ```python
   from pyspark.sql import SparkSession, Row

   spark = SparkSession.builder.appName("ExemploGitColab").getOrCreate()

   dados = [Row(nome="Elias", idade=35),
            Row(nome="Marina", idade=29),
            Row(nome="Lucas", idade=41)]

   df = spark.createDataFrame(dados)
   df_transformado = df.withColumn("idade_em_5_anos", df.idade + 5)
   df_transformado.show()
   ```
3. Criar branch:

   ```bash
   git checkout -b feature/pyspark_colab
   ```
4. Adicionar e commitar:

   ```bash
   git add exemplo_pyspark_colab.py
   git commit -m "Adiciona exemplo PySpark executável no Colab"
   git push -u origin feature/pyspark_colab
   ```
5. Criar Pull Request no GitHub → Merge na `main`.

---

## Observações Finais

* Sempre use **mensagens de commit claras**.
* Cada feature ou alteração deve ter sua **própria branch**.
* Use Pull Requests para revisão de código e histórico organizado.
* Depois do merge, delete a branch para manter o repositório limpo:

  ```bash
  git branch -d feature/pyspark_colab
  git push origin --delete feature/pyspark_colab
  ```

---


