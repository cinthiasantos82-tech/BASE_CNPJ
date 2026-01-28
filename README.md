 (cd "$(git rev-parse --show-toplevel)" && git apply --3way <<'EOF' 
diff --git a/README.md b/README.md
new file mode 100644
index 0000000000000000000000000000000000000000..343e12366582451d97f3ce47a8843dfc63f9b71c
--- /dev/null
+++ b/README.md
@@ -0,0 +1,50 @@
+# Extração de Regime Tributário (CNPJ)
+
+Este repositório contém um script para identificar o regime tributário das empresas
+ao combinar quatro bases (Imunes e Isentas, Lucro Arbitrado, Lucro Presumido e
+Lucro Real) com a base principal de CNPJ.
+
+## Requisitos
+
+* Python 3.9+
+* pandas
+
+## Uso
+
+## Como baixar sem usar Git
+
+Se você não quiser usar Git, pode baixar o repositório como ZIP:
+
+1. Acesse a página do repositório no navegador.
+2. Clique em **Code** → **Download ZIP**.
+3. Extraia o ZIP em uma pasta local.
+4. Abra o terminal na pasta extraída.
+
+Depois disso, siga as instruções de **Uso** abaixo.
+
+```bash
+python scripts/extrair_regime_tributario.py \
+  --imunes-isentas caminho/IMUNES_ISENTAS.csv \
+  --lucro-arbitrado caminho/LUCRO_ARBITRADO.csv \
+  --lucro-presumido caminho/LUCRO_PRESUMIDO.csv \
+  --lucro-real caminho/LUCRO_REAL.csv \
+  --cnpj-base caminho/CNPJ.csv \
+  --output saida/regime_tributario.csv
+```
+
+Se as colunas de CNPJ tiverem nomes diferentes, informe-as:
+
+```bash
+python scripts/extrair_regime_tributario.py \
+  --imunes-isentas IMUNES_ISENTAS.csv \
+  --lucro-arbitrado LUCRO_ARBITRADO.csv \
+  --lucro-presumido LUCRO_PRESUMIDO.csv \
+  --lucro-real LUCRO_REAL.csv \
+  --cnpj-base CNPJ.csv \
+  --regime-cnpj-column cnpj_basico \
+  --cnpj-base-column cnpj \
+  --output regime_tributario.csv
+```
+
+O script tenta inferir automaticamente a coluna de CNPJ procurando por um campo
+com “cnpj” no nome da coluna e normaliza para 14 dígitos.
 
EOF
)
