# Documentação para a Importação via XML para Imóveis na OLX

Este manual tem como objetivo auxiliar a implantação de importação de anúncios de XML para o segmento de Imóveis.

O formato de XML aceito pela OLX é específico para o portal OLX Brasil. Ele é baseado no formato ZAP, logo é possível se basear no XML para o ZAP para montar um XML para a OLX. Dito isso, é importante que você siga esse padrão descrito nessa documentação.

Feita a avaliação de que os anúncios poderão ser adaptados ao formato XML e disponibilizados em uma URL, o cliente entrará em contato com a OLX informando que seus anúncios estão disponíveis para cadastro, solicitando a URL que contém os anúncios à empresa que as disponibiliza ou ao seu departamento de tecnologia. 

Para a integração via Arquivo, a OLX vai consultar periodicamente (mínimo de uma vez por dia) o arquivo disponibilizado pelo anunciante. Para isso, caberá ao anunciante (junto com seu integrador, quando isso for aplicável) disponibilizar uma URL onde esse arquivo estará sempre disponível. O formato do encoding do arquivo a ser enviado deverá ser UTF8:

```xml
<?xml version="1.0" encoding="utf-8"?>
```

## Parâmetros

Para a montagem do JSON, é necessário respeitar parâmetros genéricos e específicos de cada categoria e/ou subcategoria. Os parâmtros básicos são os seguintes:

| Tag XML| Tamanho | Obrigatório? | Descrição|
|-------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|--------------|---------------------------------------------------------------------------------------------|
| `<CodigoImovel>` | 20 | Sim | Identificador do anúncio para o anunciante/integrador. Não pode haver `<CodigoImovel>` repetido no arquivo. |
| `<TituloAnuncio>` | 90 | Não<sup>1</sup> | Título do Imóvel, que será mostrado na listagem de resultados. |
| `<SubTipoImovel>` | 40 | Sim | Essa tag determina a categoria onde o anúncio será inserido na OLX. Para saber os valores possíveis, consulte a documentação de cada subcategoria. |
| `<CEP>` | 8 | Sim | Código de localização do imóvel. |
| `<PrecoVenda>` | 8 | Sim | Valor de venda do imóvel. Número inteiro, sem parte decimal, sem separador de milhares. |
| `<PrecoLocacao>` | 8 | Sim | Valor de aluguel do imóvel. Número inteiro, sem parte decimal, sem separador de milhares |
| `<PrecoCondominio>` | 8 | Não | Valor do condomínio do imóvel. Número inteiro, sem parte decimal, sem separador de milhares. |
| `<ValorIPTU>` | 20 | Não | Valor mensal do IPTU do imóvel. Número inteiro, sem parte decimal, sem separador de milhares. |
| `<AreaTotal>` | 15 | Não | Tamanho em metros quadrados do imóvel. Número inteiro, sem parte decimal. |
| `<AreaUtil>` | 15 | Não | Tamanho em metros quadrados do imóvel. Número inteiro, sem parte decimal. |
| `<Observacao>` | 6000 | Sim | Descrição do anúncio. Usar `\n` para quebra de linha. |
| `<Foto>` `<NomeArquivo>` | 255 | Não | Nome da imagem no banco de dados do cliente. |
| `<Foto>` `<URLArquivo>` | 255 | Não | Link em que a imagem está hospedada. |
| `<Foto>` `<Principal>` | 1 | Não | Valor `1` caso a imagem seja a imagem principal do anúncio. |

<sup>1</sup> Caso não seja enviado nenhum valor para `<TituloAnuncio>` (Título de Anúncio), será montado um título para o anúncio baseado no `<SubTipoImovel>` e outros atributos, como número de quartos, localização, etc. 

Além desses parâmetros básicos, cada subcategoria sem parâmetros específicos. A descrição destes parâmetros e XMLs de exemplo encontram-se na página de cada subcategoria:

- [Apartamentos](sub_apartments.md)
- [Casas](sub_house.md)
- [Comércio e indústria](sub_commercial.md)
- [Terrenos, sítios e fazendas](sub_land.md)

As subcategorias `Aluguel de Quartos` e `Temporada` não são suportadas pela integração via XML.


## Inferência de Inserção, Edição e Deleção de Anúncios

A OLX funciona com um modelo de inserção paga de anúncios. Para a importação de anúncios via arquivo, a OLX vai inferir que há uma nova inserção quando houver um anúncio com identificador inédito. No caso de XML, o parâmetro utilizado para inferir inserção de um anúncio é o `CodigoImovel`.

Se um anúncio com um identificador já existente estiver no arquivo em uma nova importação, não realizaremos nenhuma operação, a menos que haja alguma alteração nas outras informações desses anúncio. Nesse caso, trataremos a operação como uma edição (e não inserção).

Para que ocorra a deleção de um anúncio, basta que ele deixe de existir no arquivo e, no próximo processamento dessa carga vamos inferir que esse anúncio deve ser removido. 

**Importante**: se um anúncio for removido e no próximo processamento ele voltar a aparecer no arquivo (ou, especificamente, se um determinado identificador deixar de existir no arquivo e, em outra importação, voltar a aparecer, vamos inferir (e, portanto, contabilizar) uma nova inserção. Por isso é crítico que um anúncio sempre esteja disponível com o mesmo identificador no arquivo e só deixe de aparecer quando de fato tivermos que removê-lo do seu inventário.
