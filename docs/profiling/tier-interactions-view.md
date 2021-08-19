---
title: Katman Etkileşimleri Görünümü | Microsoft Docs
description: Katman etkileşim profili oluşturmanın, veritabanlarıyla iletişim kuran çok katmanlı uygulamaların işlevlerinde yürütme süreleri hakkında nasıl bilgi sağladığını öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.tierinteraction
helpviewer_keywords:
- Tier Interactions view
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 16d2e3d6dd64ff5827376ffba1f1ee65f6b9860e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141109"
---
# <a name="tier-interactions-view"></a>Katman Etkileşimleri Görünümü

Katman etkileşimi profili oluşturma, aracılığıyla veritabanlarıyla iletişim kuran çok katmanlı uygulamaların işlevlerinde yürütme süreleri hakkında ek bilgi [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] sağlar. Veriler yalnızca zaman uyumlu işlev çağrıları için toplanır.

**Gereksinimler**

- Visual Studio Enterprise

Etkileşimler Görünümü katman etkileşim verilerini iki bölmede görüntüler:

- Ana bölme hiyerarşik bir ağaçtır. Üst düzey satır, bir sayfanın veya bir sürecin veritabanı bağlantıları için [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] toplanan verileri içerir. Alt düğümler, üst öğenin veritabanı bağlantıları için toplanan verileri içerir.

- Ana bölmede bir veritabanı çağrı düğümüne tıklarken, veritabanı çağrısı örneğine ilişkin veriler ayrıntılar bölmesinde görüntülenir.

  Saat, milisaniye sayısı veya CPU saati saat sayısı olarak görüntülenir. Görüntülenen zaman birimini değiştirmek için Araçlar  **menüsüne** tıklayın, Seçenekler'e tıklayın ve ardından Zaman değerlerini **göster seçenekleri'ne** tıklayın.

## <a name="master-pane"></a>Ana bölme

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|- Üst düzey bir satır için, profili yapılan işlem veya Web sayfasının adı.<br />- Veritabanı bağlantı satırı için veritabanını barındıran sunucunun adı.|
|**Veritabanı**|Veritabanının adı (yalnızca veritabanı bağlantı satırları).|
|**Sayısı**|İşlem, Web sayfası veya veritabanı bağlantısı tarafından oluşturulan isteklerin toplam sayısı.|
|**Geçen Toplam Süre**|İşlemden, Web sayfasından veya veritabanı bağlantısından herhangi bir isteğin yürütülmesi için harcanan toplam süre.|
|**Geçen En Uzun Süre**|İşlemden, Web sayfasından veya veritabanı bağlantısından herhangi bir isteğin yürütülmesi için harcanan en uzun süre.|
|**En Az Geçen Süre**|İşlemden, Web sayfasından veya veritabanı bağlantısından herhangi bir isteğin yürütülmesi için harcanan minimum süre.|
|**Geçen Ortalama Süre**|İşlemden, Web sayfasından veya veritabanı bağlantısından bir isteği yürütmek için harcanan ortalama süre.|

## <a name="database-connection-details-pane"></a>Veritabanı Bağlantı Ayrıntıları bölmesi

|Sütun|Açıklama|
|------------|-----------------|
|**Komut Metni**|İsteğin SQL sorgusunu görüntüler.|
|**Sorgu Sayısı**|Sorgunun çalıştırıma sayısı.|
|**Geçen Toplam Süre**|Sorgu örneklerinin yürütülmesi için harcanan toplam süre.|
|**Geçen En Uzun Süre**|Sorgunun herhangi bir örneğini yürütmek için harcanan en uzun süre.|
|**En Az Geçen Süre**|Sorgunun herhangi bir örneğini yürütmek için harcanan minimum süre.|
|**Geçen Ortalama Süre**|Sorgunun bir örneğini yürütmek için harcanan ortalama süre.|
