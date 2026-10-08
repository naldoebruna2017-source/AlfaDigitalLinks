# Review Link Pro

Crie uma aplicação SaaS web chamada "Alfa Review CTA".

OBJETIVO DO SISTEMA

A ferramenta permitirá que um cliente crie links personalizados para campanhas de avaliação no Google.

O usuário informa:

1. Link de avaliação do Google

2. Título da CTA

3. Subtítulo da CTA

4. Link do botão CTA, normalmente WhatsApp

5. Link do perfil do Instagram para o próximo passo

6. Meta Pixel ID

7. Google Analytics Measurement ID

O sistema deverá gerar um link/campanha própria que possa ser colocado em um QR Code.

FLUXO PRINCIPAL

O fluxo desejado é:

QR CODE / LINK

↓

ALFA REVIEW CTA

↓

Página de avaliação do Google

↓

Usuário realiza a avaliação no Google

↓

Retorna para uma página intermediária do Alfa Review CTA

↓

Página de agradecimento

↓

Botão "Conheça nosso Instagram"

↓

Redirecionamento para o Instagram

IMPORTANTE SOBRE O GOOGLE

Não tente detectar tecnicamente se o usuário realmente publicou uma avaliação no Google.

O Google não fornece para essa aplicação um callback confiável dizendo que determinada pessoa terminou e publicou uma avaliação.

Portanto:

- Nunca afirmar que o sistema confirmou que a avaliação foi publicada.

- Nunca usar linguagem como "Detectamos sua avaliação".

- Nunca tentar manipular a avaliação.

- Nunca filtrar usuários por avaliação positiva ou negativa.

- Não exigir avaliação positiva para liberar qualquer benefício.

- A página intermediária deve deixar claro que o usuário pode continuar quando terminar sua interação com o Google.

A aplicação deve ser construída de forma compatível com as políticas do Google.

====================================

PAINEL ADMINISTRATIVO

====================================

Criar dashboard moderno e responsivo.

Menu lateral:

- Dashboard

- Campanhas

- Criar campanha

- Analytics

- Configurações

====================================

CRIAR CAMPANHA

====================================

Criar formulário:

Nome da campanha

[________________________]

Nome do estabelecimento

[________________________]

LINK DE AVALIAÇÃO DO GOOGLE

[________________________]

Exemplo:

https://g.page/r/XXXXXXXX/review

CTA

Título da CTA

[Quer criar sua própria loja virtual?]

Subtítulo da CTA

[Tenha uma loja profissional e venda seus produtos 24 horas por dia.]

Texto do botão

[Quero saber mais]

LINK DO CTA

[https://wa.me/...]

INSTAGRAM

Link do Instagram

[https://instagram.com/...]

Texto da página de Instagram

[Conheça também nosso Instagram]

Botão:

[Conhecer Instagram]

====================================

TRACKING

====================================

Criar seção:

META PIXEL

Meta Pixel ID

[________________]

Google Analytics

Measurement ID

[________________]

Permitir que o usuário deixe esses campos vazios.

Se preenchidos, inserir os respectivos scripts apenas nas páginas da campanha.

Não inserir scripts duplicados.

Registrar eventos importantes:

- page_view

- google_click

- cta_view

- cta_click

- instagram_view

- instagram_click

Para Meta Pixel utilizar eventos equivalentes quando apropriado.

Exemplo:

PageView

ViewContent

Lead

Contact

Não inventar eventos falsos.

====================================

EXPERIÊNCIA DO USUÁRIO

====================================

A página pública deve ser extremamente mobile-first.

A maioria dos acessos virá de QR Codes escaneados pelo celular.

Quando o usuário acessar:

/r/{slug}

o sistema deverá registrar o acesso e apresentar a experiência da campanha.

Primeiro mostrar uma pequena página/intersticial explicando:

"Obrigado por visitar nossa loja!"

"Queremos saber como foi sua experiência."

Botão:

"Deixar avaliação no Google"

Ao clicar:

abrir o link de avaliação do Google.

Preferencialmente abrir em nova aba/janela quando possível, sem impedir o usuário de continuar.

====================================

CTA

====================================

A CTA da Alfa Digital deve aparecer de maneira elegante e não invasiva.

Exemplo:

---

Quer levar sua loja para a internet?

Crie uma loja virtual profissional e venda 24 horas por dia.

[ QUERO SABER MAIS ]

---

A CTA deve poder aparecer:

- na parte inferior da tela

- como barra fixa

- como card flutuante

Criar opção de configuração:

Posição:

[Inferior]

[Superior]

[Flutuante]

No mobile, a CTA deve ocupar no máximo aproximadamente 20-25% da tela.

Deve possuir botão para minimizar/fechar.

====================================

PÁGINA APÓS O GOOGLE

====================================

Como não é possível confirmar automaticamente que a avaliação foi publicada, criar uma página intermediária específica.

URL:

/r/{slug}/continue

Conteúdo:

"Obrigado pela sua visita!"

"Sua opinião é muito importante para nós."

Botão:

"Conhecer nosso Instagram"

Ao clicar:

registrar evento:

instagram_click

e redirecionar para o Instagram configurado pelo estabelecimento.

Adicionar também:

"Voltar para o Google"

caso o usuário queira continuar a interação.

====================================

RETORNO DO GOOGLE

====================================

Criar mecanismo de retorno baseado no fluxo da campanha.

Quando possível, utilizar uma página intermediária antes do Google para manter o estado da sessão.

IMPORTANTE:

Não afirmar que o usuário avaliou.

O sistema deve tratar o retorno simplesmente como:

"Usuário retornou ao fluxo"

e não como:

"Avaliação confirmada".

====================================

LINK PERSONALIZADO

====================================

Cada campanha deve possuir um slug único.

Exemplo:

https://go.alfadigital.com.br/r/moda-xyz

ou:

https://go.alfadigital.com.br/r/abc123

Criar botão:

"Copiar link"

"Gerar QR Code"

"Visualizar campanha"

====================================

QR CODE

====================================

Gerar QR Code automaticamente para cada campanha.

O QR Code deve apontar para:

https://go.alfadigital.com.br/r/{slug}

Permitir:

- visualizar

- baixar PNG

- copiar link

Criar opção para gerar QR Code em alta resolução.

====================================

ANALYTICS

====================================

Dashboard por campanha:

Visualizações

Cliques em "Avaliar no Google"

Visualizações da CTA

Cliques na CTA

Retornos ao fluxo

Cliques no Instagram

Mostrar:

CTR da CTA

Taxa de clique no Instagram

Taxa de clique para Google

Exemplo:

Visualizações

1.248

Cliques Google

742

Visualizações CTA

1.102

Cliques WhatsApp

186

Cliques Instagram

94

====================================

ANALYTICS POR PERÍODO

====================================

Filtros:

Hoje

7 dias

30 dias

90 dias

Personalizado

Gráficos:

- acessos por dia

- cliques no Google

- cliques na CTA

- cliques no Instagram

====================================

MULTI-TENANT

====================================

Preparar arquitetura para SaaS.

Cada usuário deve possuir:

workspace

Dentro do workspace:

campaigns

links

events

settings

Nenhum usuário pode acessar dados de outro workspace.

Utilizar Supabase Auth + PostgreSQL + Row Level Security.

====================================

BANCO DE DADOS

====================================

Criar tabelas:

profiles

id

user_id

name

created_at

workspaces

id

name

owner_id

created_at

campaigns

id

workspace_id

name

business_name

slug

google_review_url

cta_title

cta_subtitle

cta_button_text

cta_url

instagram_url

instagram_button_text

cta_position

meta_pixel_id

ga_measurement_id

status

created_at

updated_at

events

id

campaign_id

event_type

session_id

device

browser

os

referrer

country

created_at

analytics_daily

id

campaign_id

date

page_views

google_clicks

cta_views

cta_clicks

instagram_clicks

====================================

SEGURANÇA

====================================

Utilizar:

Supabase Authentication

Row Level Security

Validação de URLs

Sanitização de inputs

Rate limiting quando necessário

Proteção contra XSS

Proteção contra scripts arbitrários

IMPORTANTE:

Nunca permitir que o usuário injete JavaScript personalizado diretamente no HTML.

Meta Pixel e Google Analytics devem ser configurados somente pelos IDs próprios dos campos.

Validar:

Meta Pixel ID

GA Measurement ID

Google URL

Instagram URL

CTA URL

====================================

DESIGN

====================================

Interface SaaS premium.

Estilo:

Alfa Digital

moderno

minimalista

profissional

mobile-first

Cores predominantes:

Azul escuro

Branco

Azul vibrante

Detalhes em verde para WhatsApp

Usar:

Cards

Dashboard

Gráficos

Badges

Modais

Toast notifications

Utilizar Tailwind CSS + shadcn/ui.

====================================

TECNOLOGIA

====================================

Frontend:

React

TypeScript

Vite

Tailwind CSS

shadcn/ui

Backend:

Supabase

PostgreSQL

Supabase Auth

Supabase Edge Functions quando necessário

QR Code:

usar uma biblioteca confiável para geração de QR Codes.

====================================

ROTAS

====================================

/login

/dashboard

/campaigns

/campaigns/new

/campaigns/:id

/campaigns/:id/analytics

/settings

/r/:slug

/r/:slug/continue

====================================

REDIRECIONAMENTO

====================================

O sistema deve registrar o evento ANTES do redirecionamento sempre que tecnicamente possível.

Exemplo:

Usuário clica:

"Deixar avaliação no Google"

Sistema registra:

google_click

Depois abre:

google_review_url

Ao clicar:

"Conhecer nosso Instagram"

Sistema registra:

instagram_click

Depois redireciona para:

instagram_url

====================================

IMPORTANTE SOBRE A CTA

====================================

A CTA é da Alfa Digital e tem objetivo comercial.

Ela deve aparecer como uma camada independente da página do Google.

Não modificar o conteúdo do Google.

Não tentar inserir código dentro do Google.

Não tentar controlar a interface do Google.

Não usar iframe para tentar manipular a página do Google.

A experiência deve funcionar como uma página intermediária/overlay própria do Alfa Link.

Se uma página externa não permitir embedding, nunca quebrar a campanha.

Usar o modo de redirecionamento/intermediário.

====================================

OBJETIVO FUTURO

====================================

Preparar arquitetura para futuramente permitir:

- vários estabelecimentos

- vários links por estabelecimento

- QR Codes personalizados

- domínio próprio

- planos Free / Pro / Agency

- white label

This project was built with [Lovable](https://lovable.dev).

**Live app**: https://alpha-review-boost.lovable.app

## Build with Lovable

Continue developing this project in the [Lovable editor](https://lovable.dev/projects/a4e8bf8f-917b-48ee-a95b-ddd0fee18115).

- **Ship faster**: describe what you want to build and Lovable handles the code.
- **Stay in sync**: every change made in Lovable is committed straight to this repository.
- **Full ownership**: this code is yours. Push to `main` on GitHub and your changes sync back into Lovable, ready for your next prompt.

## Development

Prefer working locally? You need Node.js and npm — [install with nvm](https://github.com/nvm-sh/nvm#installing-and-updating).

```sh
git clone <this-repository-url>
cd <repository-name>
npm i
npm run dev
```
