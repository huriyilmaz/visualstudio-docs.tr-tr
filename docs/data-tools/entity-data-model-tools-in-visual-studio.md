---
title: Entity Framework Tools
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6efcd0ca4e8274df7667b5a5b2b75020def8c358
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72807020"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Visual Studio 'da Entity Framework Tools

Entity Framework, .NET geliştiricilerin, etki alanına özgü nesneleri kullanarak ilişkisel verilerle çalışmasını sağlayan, nesne ilişkisel bir eşleme teknolojisidir. Genellikle geliştiricilerin yazmak zorunda olduğu çoğu veri erişim koduna yönelik gereksinimi ortadan kaldırır. Entity Framework, yeni .NET uygulamaları için önerilen nesne ilişkisel eşleme (ORM) modelleme teknolojisidir.

Entity Framework Tools, Entity Framework (EF) uygulamaları oluşturmanıza yardımcı olacak şekilde tasarlanmıştır. Entity Framework için tam belgeler şunlardır: [genel bakış-EF 6](/ef/ef6/).

  > [!NOTE]
  > Bu sayfada açıklanan Entity Framework Tools, EF Core desteklenmeyen *. edmx* dosyalarını oluşturmak için kullanılır. Varolan bir veritabanından bir EF Core modeli oluşturmak için bkz. [ters mühendislik-EF Core](/ef/core/managing-schemas/scaffolding). EF 6 ve EF Core arasındaki farklar hakkında daha fazla bilgi için bkz. [EF 6 ve EF Core karşılaştırma](/ef/efcore-and-ef6/).

Entity Framework Tools, var olan bir veritabanından *kavramsal model* oluşturabilir ve ardından kavramsal modelinizi grafiksel olarak görselleştirebilir ve düzenleyebilirsiniz. Ya da önce bir kavramsal model oluşturabilir, ardından modelinizi destekleyen bir veritabanı oluşturabilirsiniz. Her iki durumda da, temel alınan veritabanı değiştiğinde modelinizi otomatik olarak güncelleştirebilir ve uygulamanız için otomatik olarak nesne katmanı kodu oluşturur. Veritabanı oluşturma ve nesne katmanı kod üretimi özelleştirilebilir.

Entity Framework araçları, Visual Studio Yükleyicisi **veri depolama ve işleme** iş yükünün parçası olarak yüklenir. Ayrıca, bunları **SDK 'lar, kitaplıklar ve çerçeveler** kategorisi altında ayrı bir bileşen olarak da yükleyebilirsiniz.

Visual Studio 'da Entity Framework araçları oluşturan özel araçlar şunlardır:

- Varlıklar, ilişkilendirmeler, eşlemeler ve devralma ilişkilerini görsel olarak oluşturmak ve değiştirmek için [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] tasarımcısını** (**Entity Desisgner**) kullanabilirsiniz. **Entity Desisgner** Ayrıca [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] veya [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nesne katmanı kodu oluşturur.

- Mevcut bir veritabanından kavramsal model oluşturmak ve uygulamanıza veritabanı bağlantı bilgilerini eklemek için **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] sihirbazını** kullanabilirsiniz.

- Önce kavramsal model oluşturmak için **veritabanı oluşturma Sihirbazı 'nı** kullanabilir, sonra da modeli destekleyen bir veritabanı oluşturabilirsiniz.

- Temel veritabanında değişiklik yapıldığında kavramsal modelinizi, depolama modelinizi ve eşlemelerinizi güncelleştirmek için **model güncelleştirme sihirbazını** kullanabilirsiniz.

  > [!NOTE]
  > Visual Studio 2010 ' den başlayarak Entity Framework araçları [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)]desteklemez.

Araçlar bir *. edmx* dosyası oluşturur veya değiştirir. Bu *. edmx* dosyası kavramsal modeli, depolama modelini ve bunlar arasındaki eşlemeleri açıklayan bilgiler içerir. Daha fazla bilgi için bkz. [edmx](/ef/ef6/).

[Entity Framework güç araçları](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) , varlık veri modeli kullanan uygulamalar oluşturmanıza yardımcı olur. Güç araçları kavramsal model oluşturabilir, var olan bir modeli doğrulayabilir, kavramsal modeli temel alan nesne sınıfları içeren kaynak kodu dosyaları üretebilir ve modelin oluşturduğu görünümleri içeren kaynak kodu dosyaları üretebilir. Ayrıntılı bilgi için bkz. [önceden oluşturulmuş eşleme görünümleri](https://docs.microsoft.com/ef/ef6/fundamentals/performance/pre-generated-views).

## <a name="related-topics"></a>İlgili konular

| Başlık | Açıklama |
| - | - |
| [ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index) | Uygulamaları oluşturmak için [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] sağladığı [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] araçların nasıl kullanılacağını açıklar. |
| [Varlık Veri Modeli](/dotnet/framework/data/adonet/entity-data-model) | [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]oluşturulan uygulamalar tarafından kullanılan verilerle çalışmaya yönelik bağlantılar ve bilgiler sağlar. |
| [Entity Framework (EF) belgeleri)](/ef/ef6/get-started) | Entity Framework en iyi duruma getirmenize yardımcı olmak için bir videolar, öğreticiler ve gelişmiş belge dizini sağlar. |
| [ASP.NET 5 uygulamasını yeni veritabanına](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html) | Entity Framework 7 kullanarak yeni bir ASP.NET 5 uygulamasının nasıl oluşturulduğunu açıklar. |

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)