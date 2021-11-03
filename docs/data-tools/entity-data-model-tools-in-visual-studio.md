---
title: Entity Framework Tools
description: Visual Studio Entity Framework Tools anlayın. Entity Framework Tools, Entity Framework (EF) uygulamaları oluşturmanıza yardımcı olacak şekilde tasarlanmıştır.
ms.custom: SEO-VS-2020
ms.date: 11/01/2021
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c7b9d4fceff3b4063856fe7df88bf816fdfb70bf
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131126499"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Visual Studio Entity Framework Tools

Entity Framework, .NET geliştiricilerin, etki alanına özgü nesneleri kullanarak ilişkisel verilerle çalışmasını sağlayan, nesne ilişkisel bir eşleme teknolojisidir. Geliştiricilerin genellikle yazması gereken çoğu veri erişim kodu gereksinimini ortadan kaldırır. Entity Framework, yeni .NET uygulamaları için önerilen nesne ilişkisel eşleme (ORM) modelleme teknolojisidir.

Entity Framework Tools, Entity Framework (EF) uygulamaları oluşturmanıza yardımcı olacak şekilde tasarlanmıştır. Entity Framework için tam belgeler şunlardır: [genel bakış-EF 6](/ef/ef6/).

  > [!NOTE]
  > Bu sayfada açıklanan Entity Framework Tools, EF Core desteklenmeyen *. edmx* dosyalarını oluşturmak için kullanılır. Varolan bir veritabanından bir EF Core modeli oluşturmak için bkz. [ters mühendislik-EF Core](/ef/core/managing-schemas/scaffolding). EF 6 ve EF Core arasındaki farklar hakkında daha fazla bilgi için bkz. [EF 6 ve EF Core karşılaştırma](/ef/efcore-and-ef6/).

Entity Framework Tools, var olan bir veritabanından *kavramsal model* oluşturabilir ve ardından kavramsal modelinizi grafiksel olarak görselleştirebilir ve düzenleyebilirsiniz. Ya da önce bir kavramsal model oluşturabilir, ardından modelinizi destekleyen bir veritabanı oluşturabilirsiniz. Her iki durumda da, temel alınan veritabanı değiştiğinde modelinizi otomatik olarak güncelleştirebilir ve uygulamanız için otomatik olarak nesne katmanı kodu oluşturur. Veritabanı oluşturma ve nesne katmanı kod üretimi özelleştirilebilir.

Entity Framework araçları, Visual Studio Yükleyicisi **veri depolama ve işleme** iş yükünün parçası olarak yüklenir. Ayrıca, bunları **SDK 'lar, kitaplıklar ve çerçeveler** kategorisi altında ayrı bir bileşen olarak da yükleyebilirsiniz.

Bunlar Visual Studio Entity Framework araçları oluşturan özel araçlardır:

- [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] Tasarımcı** (**Entity Desisgner**) kullanarak varlıklar, ilişkilendirmeler, eşlemeler ve devralma ilişkilerini görsel olarak oluşturabilir ve değiştirebilirsiniz. **Entity Desisgner** Ayrıca, [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] veya [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nesne katmanı kodu oluşturur.

- **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] Sihirbazı** , mevcut bir veritabanından kavramsal bir model oluşturmak ve uygulamanıza veritabanı bağlantı bilgilerini eklemek için kullanabilirsiniz.

- Önce kavramsal model oluşturmak için **veritabanı oluşturma Sihirbazı 'nı** kullanabilir, sonra da modeli destekleyen bir veritabanı oluşturabilirsiniz.

- Temel veritabanında değişiklik yapıldığında kavramsal modelinizi, depolama modelinizi ve eşlemelerinizi güncelleştirmek için **model güncelleştirme sihirbazını** kullanabilirsiniz.

  > [!NOTE]
  > Visual Studio 2010 ' den başlayarak Entity Framework araçları desteklenmez [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)] .

Araçlar bir *. edmx* dosyası oluşturur veya değiştirir. Bu *. edmx* dosyası kavramsal modeli, depolama modelini ve bunlar arasındaki eşlemeleri açıklayan bilgiler içerir. Daha fazla bilgi için bkz. [edmx](/ef/ef6/).

[Entity Framework 6 güç araçları](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) , varlık veri modeli kullanan uygulamalar oluşturmanıza yardımcı olur. Güç araçları kavramsal model oluşturabilir, var olan bir modeli doğrulayabilir, kavramsal modeli temel alan nesne sınıfları içeren kaynak kodu dosyaları üretebilir ve modelin oluşturduğu görünümleri içeren kaynak kodu dosyaları üretebilir. Ayrıntılı bilgi için bkz. [önceden oluşturulmuş eşleme görünümleri](/ef/ef6/fundamentals/performance/pre-generated-views).

## <a name="related-topics"></a>İlgili konular

| Başlık | Açıklama |
| - | - |
| [ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index) | [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] Uygulamaları oluşturmak için sağlayan araçların nasıl kullanılacağını açıklar. |
| [Varlık Veri Modeli](/dotnet/framework/data/adonet/entity-data-model) | Üzerinde oluşturulan uygulamalar tarafından kullanılan verilerle çalışmaya yönelik bağlantılar ve bilgiler sağlar [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] . |
| [Entity Framework (EF) belgeleri)](/ef/ef6/get-started) | Entity Framework en iyi duruma getirmenize yardımcı olmak için bir videolar, öğreticiler ve gelişmiş belge dizini sağlar. |

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
