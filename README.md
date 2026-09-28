# Corte Certo

**Precifique certo. Corte certo. Lucre certo.**

Aplicação local, em português do Brasil, para organizar materiais, configurar custos e calcular cotações e pedidos de adesivos de recorte. A interface funciona em computador e celular; os dados são mantidos no armazenamento local do navegador.

## Requisitos e execução

- Node.js 18 ou superior.
- Não há dependências externas de Node para instalar.

```sh
node server.js
```

Abra http://localhost:3000. Defina `PORT` se desejar outra porta. Também é possível abrir `index.html` diretamente, embora o servidor local seja recomendado para os módulos JavaScript.

## O que funciona

- Landing page responsiva e espaço de trabalho.
- Fundo ilustrado baseado na imagem enviada, com painéis de leitura e botões translúcidos.
- CRUD de materiais com conversão de rolo para custo por m².
- Configuração de mão de obra, máquina, energia, manutenção, lâmina, overhead e desperdício.
- Calculadora reativa de cotação com custo mínimo, preço sugerido ou personalizado, lucro, margem e markup.
- Percentual de lucro sobre o custo configurável de 0% a 500%; a margem real sobre o preço e o markup (preço ÷ custo) aparecem separadamente.
- Histórico de cotações e conversão em pedido com atualização de status.
- Persistência local, exportação e restauração de backup JSON.
- Fórmulas isoladas em `src/pricing.js`.

## Testes das fórmulas

```sh
node --test tests/pricing.test.js
```

Os testes cobrem custo por m², desperdício, mão de obra, custo total, margem, markup e preço sugerido.

## Publicar a demonstração no Vercel via GitHub

Os arquivos estáticos de publicação ficam em `public/`; `vercel.json` seleciona essa pasta e o framework `Other`, sem etapa de build. Crie um repositório no GitHub, envie o projeto e importe o repositório pelo painel do Vercel. A cada push, o Vercel publicará uma nova versão. O `.gitignore` exclui o pacote temporário de Cloudflare e arquivos `.env` locais.

Esta configuração publica uma demonstração estática. O Vercel Hobby é restrito a projetos pessoais e não comerciais; confirme o plano apropriado antes de usar o Corte Certo como serviço comercial.

## Escopo e implantação

Esta entrega é uma aplicação de uso local, não um SaaS multiusuário pronto para produção. Ela não inclui cadastro/login, recuperação de senha, banco de dados compartilhado, isolamento entre contas, cobrança recorrente, painel administrativo, clientes, relatórios financeiros completos, envio de e-mail ou gateway de pagamento. Um servidor HTTP pequeno serve os arquivos da aplicação; ele não implementa APIs de negócio nem autenticação. Os dados do localStorage pertencem ao navegador e podem ser apagados pelo usuário ou pelo próprio navegador.

Não há preços definitivos de assinatura nem transações simuladas. `.env.example` registra a única configuração do servidor local. Para atender à arquitetura de produção solicitada, ainda é necessário decidir e implementar backend com PostgreSQL/Prisma, autenticação e sessões seguras, autorização por usuário, validação no servidor, armazenamento e backups, cobrança e implantação TLS. Não publique esta versão como um serviço que armazena dados sensíveis.
