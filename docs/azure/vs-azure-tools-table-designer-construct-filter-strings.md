---
title: Tablo tasarımcısı için filtre dizeleri oluşturma | Microsoft Docs
description: Tablo tasarımcısı için filtre dizeleri oluşturma
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: 4c1573690945658d090bd4bbc8e24cad533e8e72
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122098534"
---
# <a name="constructing-filter-strings-for-the-table-designer"></a>Tablo Tasarımcısı için Filtre Dizelerini Oluşturma
## <a name="overview"></a>Genel Bakış
azure tablosunda görüntülenen verileri Visual Studio **Tablo Tasarımcısı** için bir filtre dizesi oluşturun ve filtre alanına girin. Filtre dizesi söz dizimi, WCF Veri Hizmetleri tarafından tanımlanır ve where SQL benzer, ancak bir HTTP isteği aracılığıyla Tablo hizmetine gönderilir. Tablo Tasarımcısı  uygun kodlamayı sizin için işler, bu nedenle istenen bir özellik değerine göre filtrelemek için filtre alanına yalnızca özellik adını, karşılaştırma işlecini, ölçüt değerini ve isteğe bağlı olarak Boole işleci girmeniz gerekir. Depolama Services REST API Başvuru aracılığıyla tabloyu sorgulamak için bir URL oluşturursanız olduğu gibi $filter sorgu [seçeneğini dahil REST API.](/rest/api/storageservices/)

Bu WCF Veri Hizmetleri, Açık Veri [Protokolü'ne](https://www.odata.org/) (OData) dayalıdır. Filtre sistemi sorgu seçeneğiyle ilgili ayrıntılar için (**$filter),** [bkz. OData URI Kuralları belirtimi.](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)

## <a name="comparison-operators"></a>Karşılaştırma İşleçleri
Aşağıdaki mantıksal işleçler tüm özellik türleri için de kullanılabilir:

| Mantıksal işleç | Açıklama | Örnek filtre dizesi |
| --- | --- | --- |
| eq |Eşittir |City eq 'Redmond' |
| gt |Büyüktür |Fiyat gt 20 |
| ge |Büyük veya eşittir |Fiyat 10 |
| lt |Küçüktür |Price lt 20 |
| le |Küçüktür veya eşittir |Fiyat le 100 |
| ne |Eşit değildir |City ne 'London' |
| ve |And |Price le 200 and Price gt 3.5 |
| veya |Veya |Fiyat le 3,5 veya Price gt 200 |
| not |Not |isAvailable değil |

Filtre dizesi oluşturmada aşağıdaki kurallar önemlidir:

* Bir özelliği bir değerle karşılaştırmak için mantıksal işleçleri kullanın. Bir özelliği dinamik değerle karşılaştırmanın mümkün olmadığını unutmayın; ifadenin bir tarafı sabit olması gerekir.
* Filtre dizesinin tüm kısımları büyük/küçük harfe duyarlıdır.
* Filtrenin geçerli sonuçlar döndürmesi için sabit değer, özellikle aynı veri türünde olmalıdır. Desteklenen özellik türleri hakkında daha fazla bilgi için bkz. [Tablo Hizmeti Veri Modelini anlama](/rest/api/storageservices/Understanding-the-Table-Service-Data-Model).

## <a name="filtering-on-string-properties"></a>Dize Özelliklerine Göre Filtreleme
Dize özelliklerine göre filtrelenin, dize sabiti tek tırnak işaretleri içine alın.

Aşağıdaki örnek **PartitionKey** ve **RowKey özelliklerini** filtreler; filtre dizesine anahtar olmayan ek özellikler de eklenebilir:

```
PartitionKey eq 'Partition1' and RowKey eq '00001'
```

Gerekli değildir ancak her filtre ifadesini parantez içine ayazın:

```
(PartitionKey eq 'Partition1') and (RowKey eq '00001')
```

Tablo hizmetinin joker karakter sorgularını desteklemez ve sorgularda da Tablo Tasarımcısı. Ancak, istenen ön ek üzerinde karşılaştırma işleçlerini kullanarak ön ek eşleştirmesi gerçekleştirebilirsiniz. Aşağıdaki örnek, 'A' harfiyle başlayan bir LastName özelliğine sahip varlıkları döndürür:

```
LastName ge 'A' and LastName lt 'B'
```

## <a name="filtering-on-numeric-properties"></a>Sayısal Özelliklere Göre Filtreleme
Bir tamsayı veya kayan nokta sayısını filtrelemek için, s numarayı tırnak işaretleri olmadan belirtin.

Bu örnek, değeri 30'dan büyük bir Age özelliğine sahip tüm varlıkları döndürür:

```
Age gt 30
```

Bu örnek, değeri 100,25'e eşit veya 100,25'e eşit olan amountDue özelliğine sahip tüm varlıkları döndürür:

```
AmountDue le 100.25
```

## <a name="filtering-on-boolean-properties"></a>Boole Özelliklerine Göre Filtreleme
Boole değerini filtrelemek için tırnak işaretleri **olmadan true** veya **false** değerini belirtin.

Aşağıdaki örnek, IsActive özelliğinin true olarak ayar bulunduğu tüm varlıkları **döndürür:**

```
IsActive eq true
```

Bu filtre ifadesini mantıksal işleci olmadan da yazabilir. Aşağıdaki örnekte, Tablo hizmeti IsActive'in true olduğu tüm varlıkları da **geri alır:**

```
IsActive
```

IsActive'in false olduğu tüm varlıkları geri dönmek için not işlecini kullanabilirsiniz:

```
not IsActive
```

## <a name="filtering-on-datetime-properties"></a>DateTime Özelliklerine Göre Filtreleme
Bir Tarih Saat değerine göre filtrelemek için **datetime** anahtar sözcüğünü ve ardından tek tırnak işaretleriyle tarih/saat sabiti belirtin. Tarih/saat sabiti, DateTime Özellik Değerlerini Biçimlendirme konusunda açıklandığı gibi birleşik UTC [biçiminde olmalıdır.](/rest/api/storageservices/Formatting-DateTime-Property-Values)

Aşağıdaki örnek, CustomerSince özelliğinin 10 Temmuz 2008'e eşit olduğu varlıkları döndürür:

```
CustomerSince eq datetime'2008-07-10T00:00:00Z'
```
