<h1>🔍 Projeto de Busca Distribuída com Sockets - Projetc Distributed Search</h1>

<h2>📚 Descrição</h2>
<p>
  Este projeto simula um sistema de <strong>busca distribuída</strong> utilizando <strong>sockets TCP</strong> em Java 17.
  A aplicação realiza buscas por substrings nos títulos ou resumos de artigos científicos do dataset <strong>arXiv</strong>,
  dividido entre dois servidores de busca. Um servidor principal coordena o sistema e consolida os resultados para o cliente.
</p>

<h2>🧱 Arquitetura do Sistema</h2>
<pre>
Cliente <---> Servidor A <---> Servidor B
                        \
                         \--> Servidor C
</pre>

<ul>
  <li><strong>Cliente:</strong> Envia a substring de busca ao Servidor A e recebe o resultado combinado.</li>
  <li><strong>Servidor A:</strong> Coordena a comunicação entre cliente e os servidores B e C.</li>
  <li><strong>Servidor B e C:</strong> Realizam a busca localmente no dataset particionado.</li>
</ul>

<h2>📁 Estrutura do Projeto</h2>
<pre>
project-distributed-search/
├── src/
│   └── progconc_dist/
│       ├── cliente/
│       │   └── ClienteBusca.java
│       ├── servidorA/
│       │   └── ServidorA.java
│       ├── servidorB/
│       │   └── ServidorB.java
│       └── servidorC/
│           └── ServidorC.java
├── dados/
│   ├── artigos_b.json
│   └── artigos_c.json
├── CONTRIBUTING.md
├── README.md
└── pom.xml
</pre>

<h2>🚀 Iniciando o Projeto</h2>

<h3>1. Clone o repositório</h3>
<pre><code>git clone https://github.com/seuusuario/arxiv-distributed-search.git
cd arxiv-distributed-search</code></pre>

<h3>2. Como executar</h3>

<h4>Opção A: Via linha de comando</h4>
<pre><code>javac utils/*.java servidorA/*.java servidorB/*.java servidorC/*.java cliente/*.java</code></pre>

<p>Execute os servidores em terminais separados:</p>
<pre><code>
java servidorB.ServidorB
java servidorC.ServidorC
java servidorA.ServidorA
java cliente.ClienteBusca
</code></pre>

<h4>Opção B: Usando uma IDE Java (IntelliJ, Eclipse, VS Code, etc)</h4>
<ul>
  <li>Abra/import o projeto na sua IDE.</li>
  <li>Configure o JDK 17.</li>
  <li>Compile o código.</li>
  <li>Crie configurações de execução para:
    <ul>
      <li><code>servidorB.ServidorB</code></li>
      <li><code>servidorC.ServidorC</code></li>
      <li><code>servidorA.ServidorA</code></li>
      <li><code>cliente.ClienteBusca</code></li>
    </ul>
  </li>
  <li>Execute os servidores na ordem: B, C, A e Cliente.</li>
</ul>

<h2>🔎 Algoritmo de Busca Utilizado</h2>
<p>
  Utilizamos o algoritmo <strong>Knuth-Morris-Pratt (KMP)</strong>, eficiente para buscas de padrões em strings com complexidade <code>O(n + m)</code>.
</p>
<p>🔗 <a href="https://www.geeksforgeeks.org/kmp-algorithm-for-pattern-searching/">Mais sobre o algoritmo KMP</a></p>

<h2>📂 Formato dos Dados</h2>
<p>Cada arquivo JSON tem este formato:</p>
<pre><code>{
  "title": "Título do artigo",
  "abstract": "Resumo/introdução do artigo"
}</code></pre>

<h2>📡 Comunicação entre Componentes</h2>
<p>Todos os componentes se comunicam via <strong>sockets TCP</strong> usando JSON.</p>

<p><strong>Requisição:</strong></p>
<pre><code>{
  "comando": "buscar",
  "texto": "machine learning"
}</code></pre>

<p><strong>Resposta:</strong></p>
<pre><code>[
  {
    "title": "Understanding Machine Learning",
    "abstract": "This paper explores supervised learning..."
  }
]</code></pre>

<h2>✅ Casos de Teste Sugeridos</h2>
<ul>
  <li><code>learning</code> → "machine learning", "deep learning" etc.</li>
  <li><code>neural</code> → "neural networks", etc.</li>
  <li><code>graph</code> → Relacionado a grafos.</li>
</ul>

<h2>🚀 Possíveis Melhorias Futuras</h2>
<ul>
  <li>Cache de resultados no Servidor A.</li>
  <li>Threading para paralelismo.</li>
  <li>Interface gráfica para o cliente.</li>
  <li>Balanceamento de carga.</li>
  <li>Histórico de buscas.</li>
</ul>

<h2>📗 Referências</h2>
<ul>
  <li>TANENBAUM, A. S.; VAN STEEN, M. <em>Distributed Systems: Principles and Paradigms</em>. 2ª ed.</li>
  <li><a href="https://www.geeksforgeeks.org/kmp-algorithm-for-pattern-searching/">GeeksForGeeks - KMP</a></li>
  <li><a href="https://paperswithcode.com/dataset/arxiv-10">arXiv Dataset - Papers With Code</a></li>
  <li><a href="https://www.devmedia.com.br/trabalhando-com-json-em-java-o-pacote-org-json/25480">DevMedia - JSON em Java</a></li>
</ul>

<h2>👥 Participantes</h2>
<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Matrícula</th>
      <th>Função no Projeto</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Aluno 1</td><td>123456</td><td>Cliente e Servidor A</td></tr>
    <tr><td>Aluno 2</td><td>654321</td><td>Servidor B e algoritmo KMP</td></tr>
    <tr><td>Aluno 3</td><td>789456</td><td>Servidor C e manipulação JSON</td></tr>
    <tr><td>Aluno 4</td><td>112233</td><td>Documentação e testes</td></tr>
  </tbody>
</table>

<h2>📘 Histórico de Commits</h2>
<p>O histórico de desenvolvimento está disponível no repositório:<br>
🔗 <a href="https://github.com/seuusuario/arxiv-distributed-search">github.com/seuusuario/arxiv-distributed-search</a>
</p>