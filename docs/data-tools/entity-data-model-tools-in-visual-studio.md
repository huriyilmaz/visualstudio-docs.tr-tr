---
title: Entity Framework Tools
description: Bu Entity Framework Tools an Visual Studio. Entity Framework Tools, bir (EF) uygulaması Entity Framework yardımcı olacak şekilde tasarlanmıştır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 28a703518405bfedd4a786a583e8688dcb7db134
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122161981"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Entity Framework Tools Visual Studio

Entity Framework, .NET geliştiricilerinin etki alanına özgü nesneleri kullanarak ilişkisel verilerle çalışmasına olanak sağlayan bir nesne ilişkisel eşleme teknolojisidir. Geliştiricilerin genellikle yazması gereken çoğu veri erişim kodu gereksinimini ortadan kaldırır. Entity Framework yeni .NET uygulamaları için önerilen nesne ilişkisel eşleme (ORM) modelleme teknolojisidir.

Entity Framework Tools, bir (EF) uygulaması Entity Framework yardımcı olacak şekilde tasarlanmıştır. Entity Framework belgeleri şu şekildedir: [Genel Bakış - EF 6](/ef/ef6/).

  > [!NOTE]
  > Bu Entity Framework Tools açıklanan dosyalar, bu dosyalarda desteklenen *.edmx* dosyaları oluşturmak EF Core. Mevcut veritabanından EF Core modeli oluşturmak için bkz. [Tersine Mühendislik - EF Core.](/ef/core/managing-schemas/scaffolding) EF 6 ile EF Core arasındaki farklar hakkında daha fazla bilgi için bkz. [EF 6 ile EF Core.](/ef/efcore-and-ef6/)

Bu Entity Framework Tools, var olan bir veritabanından kavramsal *bir model* oluşturabilir ve ardından kavramsal modelinizi grafiksel olarak görselleştirebilirsiniz ve düzenleyebilirsiniz. Veya grafiksel olarak önce kavramsal bir model oluşturabilir ve ardından modelinizi destekleyen bir veritabanı oluşturabilirsiniz. Her iki durumda da, temel alınan veritabanı değişirken modelinizi otomatik olarak güncelleştirebilir ve uygulamanız için otomatik olarak nesne katmanı kodu oluşturabilirsiniz. Veritabanı oluşturma ve nesne katmanı kod oluşturma özelleştirilebilir.

Entity Framework araçları, veri depolama ve işleme iş **yükünün bir parçası** olarak Visual Studio Yükleyicisi. Ayrıca, bunları TEK bir bileşen olarak **DADK'ler,** kitaplıklar ve çerçeveler kategorisi altında yükleyebilirsiniz.

Aşağıdaki araçlar, Entity Framework araçları Visual Studio:

- Varlıkları, [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] ilişkilendirmeleri,** **eşlemeleri ve** devralma ilişkilerini görsel olarak oluşturmak ve değiştirmek için Tasarımcı 'Entity Desisgner ) kullanabilirsiniz. Uygulama **Entity Desisgner** veya nesne [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] katmanı kodu da [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] oluşturur.

- Var olan bir **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] veritabanından** kavramsal model oluşturmak ve uygulamanıza veritabanı bağlantı bilgileri eklemek için Sihirbazı kullanabilirsiniz.

- Veritabanı Oluşturma **Sihirbazı'nı kullanarak önce** kavramsal bir model oluşturabilir ve ardından modeli destekleyen bir veritabanı oluşturabilirsiniz.

- Model Güncelleştirme **Sihirbazı'nı kullanarak** kavramsal modelinizi, depolama modelinizi ve temel alınan veritabanında değişiklikler yapıldıklarında eşlemelerinizi güncelleştirebilirsiniz.

  > [!NOTE]
  > Visual Studio 2010'dan Entity Framework araçları [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)] desteklemez.

Araçlar bir *.edmx dosyası üretir veya* değiştirir. Bu *.edmx* dosyası kavramsal modeli, depolama modelini ve aralarındaki eşlemeleri açıklayan bilgiler içerir. Daha fazla bilgi için bkz. [EDMX](/ef/ef6/).

[Entity Framework Power Tools,](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) power tools'ları kullanan uygulamalar Varlık Veri Modeli. Güç araçları kavramsal bir model oluşturabilir, var olan bir modeli doğrular, kavramsal modeli temel alan nesne sınıflarını içeren kaynak kod dosyaları oluşturabilir ve modelin ürettiği görünümleri içeren kaynak kodu dosyaları üretebilir. Ayrıntılı bilgi için [bkz. Önceden Oluşturulmuş Eşleme Görünümleri.](/ef/ef6/fundamentals/performance/pre-generated-views)

## <a name="related-topics"></a>İlgili konular

| Başlık | Açıklama |
| - | - |
| [ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index) | Uygulama oluşturmak için [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] araçları kullanma hakkında bilgi [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] sağlar. |
| [Varlık Veri Modeli](/dotnet/framework/data/adonet/entity-data-model) | üzerinde yerleşik uygulamalar tarafından kullanılan verilerle çalışmaya ilişkin bağlantılar ve bilgiler [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] sağlar. |
| [Entity Framework (EF) Belgeleri)](/ef/ef6/get-started) | Videolardan, öğreticilerden ve gelişmiş belgelerden bir dizine sahip olmak, bu hizmetlerden en iyi şekilde Entity Framework. |
| [ASP.NET 5 Uygulamayı Yeni Veritabanına](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html) | Entity Framework 7 kullanarak ASP.NET 5 uygulaması oluşturma hakkında Entity Framework açıklar. |

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
