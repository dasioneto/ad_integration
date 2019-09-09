# Categoria `Apartamentos`

Para que seu anúncio apareça na categoria `Apartamentos` na OLX Brasil, é necessário que a tag `<SubTipoImovel>` seja preenchida com algum dos valores da tabela abaixo.

Além disso, o `<SubTipoImovel>` vai compor o título do anúncio que a OLX vai gerar automaticamente para seu anúncio, caso não seja enviado o `<TituloAnuncio>` no XML. 

| `<SubTipoImovel>` | Título do anúncio |
|-----------------------------------|-----------------------|
| `Apartamento` | Apartamento |
| `Apartamento de Condomínio` | Apartamento |
| `Apartamento Duplex Residencial` | Apartamento |
| `Apartamento Padrão` | Apartamento |
| `Apartamento Residencial` | Apartamento |
| `Apartamento Triplex Residencial` | Apartamento |
| `Conjunto Residencial` | Apartamento |
| `Padrão` | Apartamento |
| `Cobertura` | Cobertura |
| `Cobertura Duplex` | Cobertura |
| `Cobertura Residencial` | Cobertura |
| `Cobertura Triplex` | Cobertura |
| `Penthouse Residencial` | Cobertura |
| `Flat` | Loft |
| `Flat Padrão` | Loft |
| `Flat Residencial` | Loft |
| `Loft` | Loft |
| `Loft Residencial` | Loft |
| `Kitchenette / Conjugados` | Kitchenette/conjugado |
| `Kitchenette / Studio` | Kitchenette/conjugado |
| `Kitnet` | Kitchenette/conjugado |
| `Kitnet / Conjugado` | Kitchenette/conjugado |
| `Kitnet Residencial` | Kitchenette/conjugado |
| `Studio` | Studio |

## Parâmetros específicos da categoria

| Tag XML| Tamanho | Obrigatório? | Descrição|
|-------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|--------------|---------------------------------------------------------------------------------------------|
| `<QtdVagas>` | 1 | Não | Número de vagas do imóvel. Valores de `1` a `5`. Com o valor `5`, informamos que o imóvel tem `5 vagas ou mais`.|
| `<ArCondicionado>`,<br>`<SalaGinastica>`,<br>`<ArmarioEmbutido>`,<br>`<Varanda>`,<br>`<AreaServico>`,<br>`<Churrasqueira>`,<br>`<QuartoWCEmpregada>`,<br>`<Piscina>`,<br>`<SalaoFestas>`,<br>`<Porteiro>`||| Características adicionais do imóvel. Se o imóvel tem algum desses atributos, inclua esse parâmetro com valor `1`|
| `<QtdDormitorios>` | 1 | Sim | Número de quartos do imóvel. Valores de `1` a `5`. Com o valor `5`, informamos que o imóvel tem `5 dormitórios ou mais`.|

## Exemplo de XML

```xml
<?xml version="1.0" encoding="utf-8"?>
<Carga xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    <Imoveis>
        <Imovel>
            <CodigoImovel>12345</CodigoImovel>
            <TituloAnuncio>Apartamento Espaçoso em Bairro Legal e Seguro</TituloAnuncio>
            <SubTipoImovel>Apartamento Padrão</SubTipoImovel>
            <CEP>05018000</CEP>
            <PrecoVenda>450000</PrecoVenda>
            <PrecoLocacao>0</PrecoLocacao>
            <PrecoCondominio>800</PrecoCondominio>
            <ValorIPTU>500</ValorIPTU>
            <QtdVagas>0</QtdVagas>
            <AreaUtil>67</AreaUtil>
            <AreaTotal>75</AreaTotal>
            <QtdDormitorios>3</QtdDormitorios>
            <Observacao>Residencial projetado para você em cada detalhe.\nPrédio com 2 Elevadores, Salão de Festas, Sala Fitness, Apartamento, Zelador, Guarita e Bicicletário.\nRef: 12345</Observacao>
            <Fotos>
                <Foto>
                    <NomeArquivo>Imagem Principal do Imóvel</NomeArquivo>
                    <URLArquivo>http://www.site.com.br/imagem1.jpg</URLArquivo>
                    <Principal>1</Principal>
                </Foto>
            </Fotos>
        </Imovel>
        <Imovel>
            <CodigoImovel>54321</CodigoImovel>
            <TituloAnuncio>Apartamento Espaçoso em Bairro Legal e Seguro</TituloAnuncio>
            <SubTipoImovel>Apartamento Padrão</SubTipoImovel>
            <CEP>05018000</CEP>
            <PrecoVenda>450000</PrecoVenda>
            <PrecoLocacao>0</PrecoLocacao>
            <PrecoCondominio>800</PrecoCondominio>
            <ValorIPTU>500</ValorIPTU>
            <QtdVagas>0</QtdVagas>
            <AreaUtil>67</AreaUtil>
            <AreaTotal>75</AreaTotal>
            <QtdDormitorios>3</QtdDormitorios>
            <Observacao>Residencial projetado para você em cada detalhe.\nPrédio com 2 Elevadores, Salão de Festas, Sala Fitness, Apartamento, Zelador, Guarita e Bicicletário.\nRef: 12345</Observacao>
            <Fotos>
                <Foto>
                    <NomeArquivo>Imagem Principal do Imóvel</NomeArquivo>
                    <URLArquivo>http://www.site.com.br/imagem1.jpg</URLArquivo>
                    <Principal>1</Principal>
                </Foto>
            </Fotos>
        </Imovel>
    </Imoveis>
</Carga>
```