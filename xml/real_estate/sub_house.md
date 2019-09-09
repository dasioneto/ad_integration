# Categoria `Casas`

Para que seu anúncio apareça na categoria `Casas` na OLX Brasil, é necessário que a tag `<SubTipoImovel>` seja preenchida com algum dos valores da tabela abaixo.

Além disso, o `<SubTipoImovel>` vai compor o título do anúncio que a OLX vai gerar automaticamente para seu anúncio, caso não seja enviado o `<TituloAnuncio>` no XML. 

| `<SubTipoImovel>` | Título do anúncio |
|-----------------------|--------------------|
| `Casa` | Casa |
| `Casa de Rua` | Casa |
| `Casa Padrão` | Casa |
| `Casa Padrão Térrea` | Casa |
| `Casa Residencial` | Casa |
| `Sobrado` | Casa |
| `Sobrado Residencial` | Casa |
| `Village Residencial` | Casa |
| `Casa de Condomínio` | Casa de condomínio |
| `Casa em Condomínio` | Casa de condomínio |
| `Casa de Vila` | Casa de vila |

## Parâmetros específicos da categoria

| Tag XML| Tamanho | Obrigatório? | Descrição|
|-------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|--------------|---------------------------------------------------------------------------------------------|
| `<QtdVagas>` | 1 | Não | Número de vagas do imóvel. Valores de `1` a `5`. Com o valor `5`, informamos que o imóvel tem `5 vagas ou mais`.|
| `<ArCondicionado>`,<br>`<SalaGinastica>`,<br>`<ArmarioEmbutido>`,<br>`<Varanda>`,<br>`<AreaServico>`,<br>`<Churrasqueira>`,<br>`<QuartoWCEmpregada>`,<br>`<Piscina>`,<br>`<SalaoFestas>`,<br>`<Porteiro>`||| Características adicionais do imóvel. Se o imóvel tem algum desses atributos, inclua esse parâmetro com valor `1`|
| `<QtdDormitorios>` | 1 | Sim | Número de quartos do imóvel. Valores de `1` a `5`. Com o valor `5`, informamos que o imóvel tem `5 dormitórios ou mais`.|




## Exemplo de XML