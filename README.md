
Análise de Desempenho de Lojas
Challenge Alura Store



Objetivo
O objetivo deste projeto foi ajudar o Senhor João a decidir qual das suas quatro lojas vender, com base nos dados de desempenho de cada uma. Foram avaliados: faturamento total, produtos mais e menos vendidos, satisfação dos clientes e custo médio de frete.


"""
Script: plot_faturamento_por_loja.py
Descrição: Gera o gráfico de barras "Faturamento total por loja" mostrado pelo usuário
Requisitos: pandas, matplotlib
Como usar (exemplo):
    python plot_faturamento_por_loja.py
Isso irá gerar o arquivo `Faturamento_total_por_loja.png` na mesma pasta.

Instruções rápidas para colocar no GitHub:
1. Crie um repositório (local):
   git init
   git add plot_faturamento_por_loja.py
   git commit -m "Adicionar script para gerar gráfico de faturamento por loja"
2. Conecte ao remoto e envie:
   git remote add origin <URL-do-repo>
   git branch -M main
   git push -u origin main

"""

import pandas as pd
import matplotlib.pyplot as plt
import matplotlib.ticker as mtick

# --- Dados ---
lojas = ['Loja 1', 'Loja 2', 'Loja 3', 'Loja 4']
faturamento = [1534509.12, 1488459.06, 1464025.03, 1384497.58]

df = pd.DataFrame({'Loja': lojas, 'Faturamento': faturamento})

# --- Plot ---
fig, ax = plt.subplots(figsize=(8, 5))

bars = ax.bar(df['Loja'], df['Faturamento'])

# Título e rótulos
ax.set_title('Faturamento total por loja', fontsize=14)
ax.set_ylabel('Faturamento (R$)', fontsize=12)

# Formatar eixo y como moeda (R$)
ax.yaxis.set_major_formatter(mtick.FuncFormatter(lambda x, pos: f"{x:,.0f}"))

# Anotar valores acima das barras
for bar, value in zip(bars, df['Faturamento']):
    height = bar.get_height()
    ax.annotate(f'{value:,.2f}',
                xy=(bar.get_x() + bar.get_width() / 2, height),
                xytext=(0, 6),  # deslocamento vertical
                textcoords='offset points',
                ha='center', va='bottom', fontsize=9)

plt.tight_layout()

# Salvar figura
output_path = 'Faturamento_total_por_loja.png'
plt.savefig(output_path, dpi=300)
print(f'Gráfico salvo em: {output_path}')

# Também mostrar na tela (útil em ambiente local)




Análise:
A Loja 1 apresentou o maior faturamento (R$ 1.534.509,12). Já a Loja 4 ficou em último lugar, com o valor de R$ 1.384.497,58 — indicando menor retorno financeiro.

Participação das Categorias nas Vendas
Teste

Análise:
As quatro lojas mostraram que os produtos da categoria móveis são os mais vendidos, enquanto instrumentos musicais e utilidades domésticas aparecem como as categorias menos populares. A Loja 4, apesar de boa variedade, não converteu tanto em vendas.

Média das Avaliações dos Clientes
Análise:
A Loja 3 se destacou com a avaliação mais alta (4.05), enquanto a Loja 4 ficou abaixo das demais, com uma média de 3.99.

Frete Médio por Loja
Análise:
A Loja 4 tem o frete médio mais baixo (R$ 31,28). Mesmo assim, isso não se refletiu em melhor faturamento nem em melhores avaliações.

Dispersão: Avaliação x Frete
Teste

Análise:
O gráfico mostrou que frete mais barato não garante melhores avaliações, tendo em vista que a quantidade de avaliações altas (5.0) acontecem de forma semelhante em todas as regiões, indenpendende se o frete é mais barato ou mais caro

Conclusão
Resumo final dos dados:

Loja	Faturamento Total	Produto + Vendido	Produto - Vendido	Avaliação Média	Frete Médio
Loja 1	R$ 1.534.509,12	Móveis (465)	Utilidades Domésticas (171)	3.98	R$ 34,69
Loja 2	R$ 1.488.459,06	Móveis (442)	Utilidades Domésticas (181)	4.04	R$ 33,62
Loja 3	R$ 1.464.025,03	Móveis (499)	Instrumentos Musicais (177)	4.05	R$ 33,07
Loja 4	R$ 1.384.497,58	Móveis (480)	Instrumentos Musicais (170)	3.99	R$ 31,28

Com base nessa análise, recomenda-se que o Senhor João venda a Loja 4, já que ela apresentou o desempenho mais fraco entre todas: obteve o menor faturamento, recebeu avaliações apenas medianas e, mesmo oferecendo frete mais barato, não conseguiu alcançar bons resultados de vendas.
