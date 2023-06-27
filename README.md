# Spotify-Data-Analysis
Repositório para análise de dados do Spotify para disciplina de Inteligência Artificial

## Data Scraping
[Link do Repositório](https://github.com/davitgouveia/Spotify-Data-Collection/tree/main)<br><br>
Foi utilizada a Spotify Web API para a coleta de dados, as ferramentas utilizadas foram python como linguagem de programação e as bibliotecas spotipy para interagir com a API e pandas para criação de csv. 
### Lógica de coleta
A lógica de coleta foi a seguinte, 
- Primeiramente, é realizada a busca por artistas de determinada região utilizando o search com parâmetros de tipo artista e market BR e US. Nesse endpoint conseguimos o artist_name, artist_id e artist_genre 
- Com essas informações, realizamos uma chamada para artists_top_tracks utilizando o artist_id, recebemos como resposta as top músicas do artista e as seguintes características, track_id, track_name, album_name, popularity, explicit, duration_ms.
- Então utilizamos o track_id para realizar uma última chamada, a audio_features, onde coletamos as seguintes informações, danceability, energy, key, loudness, mode, speechiness, acousticness, instrumentalness, liveness, valence, tempo, time_signature. 
Após salvar as informações em uma lista, utilizamos o pandas para criar um arquivo csv.

### Descrição das colunas:
O Spotify fornece uma grande quantidade de informações interessantes, nossos dataframes compõe das seguintes informações:
<br><br><b>track_id:</b>
O ID do Spotify da Música
<br><br><b>track_name:</b>
Nome da Música
<br><br><b>artist_name:</b>
Nome do Artista
<br><br><b>artist_genres:</b>
Gêneros do Artista
<br><br><b>album_name:</b>
Nome do álbum
<br><br><b>artist_id:</b>
O ID do Spotify do artista.
<br><br><b>popularity:</b>
A popularidade de uma música é um valor entre 0 e 100, sendo 100 o mais popular. A popularidade é calculada por algoritmo e é baseada, em grande parte, no número total de reproduções que a faixa teve e quão recentes são essas reproduções.
De um modo geral, as músicas que estão sendo muito tocadas agora terão uma popularidade maior do que as músicas que eram muito tocadas no passado. Faixas duplicadas (por exemplo, a mesma faixa de um single e um álbum) são classificadas de forma independente.
Observação: o valor da popularidade pode ser inferior à popularidade real em alguns dias: o valor não é atualizado em tempo real.
<br><br><b>duration_ms:</b>
Duração da música em milisegundos
<br><br><b>explicit:</b>
Se a música possui ou não conteúdo explícito
<br><br><b>danceability:</b>
A capacidade de dança descreve o quão adequada uma música é para dançar com base em uma combinação de elementos musicais, incluindo andamento, estabilidade do ritmo, força da batida e regularidade geral. Um valor de 0,0 é menos dançável e 1,0 é o mais dançável.
<br><br><b>energy:</b>
A energia é uma medida de 0,0 a 1,0 e representa uma medida perceptiva de intensidade e atividade. Normalmente, as faixas energéticas parecem rápidas, altas e barulhentas. Por exemplo, death metal tem alta energia, enquanto um prelúdio de Bach pontua baixo na escala. Os recursos perceptivos que contribuem para esse atributo incluem faixa dinâmica, sonoridade percebida, timbre, taxa de início e entropia geral.
<br><br><b>key:</b>
A tonalidade em que a faixa está. Os inteiros são mapeados para afinações usando a notação padrão de classe de afinação. Por exemplo. 0 = C, 1 = C♯/D♭, 2 = D e assim por diante. Se nenhuma chave foi detectada, o valor é -1
<br><br><b>loudness:</b>
O volume geral de uma faixa em decibéis (dB). Os valores de volume são calculados em média em toda a faixa e são úteis para comparar o volume relativo das faixas. Loudness é a qualidade de um som que é o principal correlato psicológico da força física (amplitude). Os valores geralmente variam entre -60 e 0 db.
<br><br><b>mode:</b>
Modo indica a modalidade (maior ou menor) de uma faixa, o tipo de escala da qual seu conteúdo melódico é derivado. Maior é representado por 1 e menor é 0.
<br><br><b>speechiness:</b>
Speechiness detecta a presença de palavras faladas em uma faixa. Quanto mais exclusivamente semelhante à fala for a gravação (por exemplo, talk show, livro de áudio, poesia), mais próximo de 1,0 será o valor do atributo. Valores acima de 0,66 descrevem faixas que provavelmente são feitas inteiramente de palavras faladas. Valores entre 0,33 e 0,66 descrevem faixas que podem conter música e fala, seja em seções ou em camadas, incluindo casos como rap. Valores abaixo de 0,33 provavelmente representam música e outras faixas não semelhantes à fala.
<br><br><b>acousticness:</b>
Uma medida de confiança de 0,0 a 1,0 se a faixa é acústica. 1.0 representa alta confiança de que a faixa é acústica.
<br><br><b>instrumentalness:</b>
Prevê se uma faixa não contém vocais. Os sons "Ooh" e "aah" são tratados como instrumentais neste contexto. Faixas de rap ou palavras faladas são claramente "vocais". Quanto mais próximo o valor da instrumentalidade estiver de 1,0, maior a probabilidade de a faixa não conter nenhum conteúdo vocal. Valores acima de 0,5 destinam-se a representar faixas instrumentais, mas a confiança é maior conforme o valor se aproxima de 1,0.
<br><br><b>liveness:</b>
Detecta a presença de uma audiência na gravação. Valores mais altos de vivacidade representam uma probabilidade maior de que a faixa tenha sido tocada ao vivo. Um valor acima de 0,8 fornece uma forte probabilidade de que a faixa esteja ativa.
<br><br><b>valence:</b>
Uma medida de 0,0 a 1,0 que descreve a positividade musical transmitida por uma faixa. Faixas com alta valência soam mais positivas (por exemplo, feliz, alegre, eufórica), enquanto faixas com baixa valência soam mais negativas (por exemplo, triste, deprimido, zangado).
<br><br><b>tempo:</b>
O andamento geral estimado de uma faixa em batidas por minuto (BPM). Na terminologia musical, tempo é a velocidade ou ritmo de uma determinada peça e deriva diretamente da duração média da batida.
<br><br><b>time_signature:</b>
Uma fórmula de compasso estimada. A fórmula de compasso (medidor) é uma convenção de notação para especificar quantas batidas há em cada compasso (ou compasso). A fórmula de compasso varia de 3 a 7, indicando fórmulas de compasso de "3/4" a "7/4".

## Coleta de dados de usuários
[Link do repositório](https://github.com/davitgouveia/Spotify-Data-Collection-APP/tree/main)<br><br>
Para coletar as Top 20 Músicas de usuários de nossa faculdade, foi criado uma aplicação Web em ReactJS que utiliza a API do Spotify para realizar a autenticação OAuth2, e assim, buscar as top 20 músicas com o endpoint https://api.spotify.com/v1/me/top/tracks
Após o usuário logar e clicar no botão de gerar os dados era baixado um arquivo JSON com as informações, que então pedimos para o usuário nos enviar o arquivo por email.
Após receber o JSON, utilizamos Python e pandas novamente para gerar os csv de dados dos usuários.
Link do website: https://spotify-data-collection-app.vercel.app/ 

Observação: Por ser uma aplicação de desenvolvimento, apenas usuários cadastrados no aplicativo Spotify são capazes de logar no nosso site, portanto foi requisitado previamente aos participantes seus emails para que sejam adicionados como beta testers.


