---
title: Katman Etkileşimleri Görünümü | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.tierinteraction
helpviewer_keywords:
- Tier Interactions view
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d188d6c3268c8ee9f066eba1b6a57e469f34a78e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778147"
---
# <a name="tier-interactions-view"></a>Katman Etkileşimleri Görünümü

Katman etkileşimi profil oluşturma, [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]veritabanları aracılığıyla iletişim sağlayan çok katmanlı uygulamaların işlevlerinde yürütme süreleri hakkında ek bilgiler sağlar. Veriler yalnızca eşzamanlı işlev çağrıları için toplanır.

**Gereksinimler**

- Visual Studio Enterprise

Etkileşimler Görünümü katman etkileşim verilerini iki bölmede görüntüler:

- Ana bölme hiyerarşik bir ağaçtır. Üst düzey satır, bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sayfanın veya işlemin veritabanı bağlantıları için toplanan verileri içerir. Alt düğümler üst veritabanı bağlantıları için toplanan verileri içerir.

- Ana bölmedeki bir veritabanı çağrı düğümününe tıkladığınızda, veritabanı çağrısı örneğine ait veriler ayrıntılar bölmesinde görüntülenir.

  Zaman milisaniye sayısı veya CPU saat tik seves sayısı olarak görüntülenir. Görüntülenen zaman birimini değiştirmek için **Araçlar** menüsünü tıklatın, **Seçenekler'i**tıklatın ve ardından seçenek **olarak göster zaman değerlerinden** birini seçin.

## <a name="master-pane"></a>Ana bölme

|Sütun|Açıklama|
|------------|-----------------|
|**Adı**|- Üst düzey bir satır için, profilli işlemin veya Web sayfasının adı.<br />- Veritabanı bağlantı satırı için, veritabanını barındıran sunucunun adı.|
|**Database**|Veritabanının adı (yalnızca veritabanı bağlantı satırları).|
|**Sayısı**|İşlem, Web sayfası veya veritabanı bağlantısı tarafından oluşturulan toplam istek sayısı.|
|**Toplam Geçen Süre**|İşlemden, Web sayfasından veya veritabanı bağlantısından herhangi bir isteği yürütmek için harcanan toplam süre.|
|**Max Geçen Süre**|İşlemden, Web sayfasından veya veritabanı bağlantısından herhangi bir isteği yürütmek için harcanan maksimum süre.|
|**Min Geçen Süre**|İşlemden, Web sayfasından veya veritabanı bağlantısından herhangi bir isteği yürütmek için harcanan minimum süre.|
|**Avg Geçen Süre**|İşlemden, Web sayfasından veya veritabanı bağlantısından gelen bir isteği yürütmek için harcanan ortalama süre.|

## <a name="database-connection-details-pane"></a>Veritabanı Bağlantı Ayrıntıları bölmesi

|Sütun|Açıklama|
|------------|-----------------|
|**Komut Metni**|İsteğin SQL sorgusu.|
|**Sorgu Sayısı**|Sorgunun kaç kez çalıştırıldığını.|
|**Toplam Geçen Süre**|Sorgu örneklerini yürütmeiçin harcanan toplam süre.|
|**Max Geçen Süre**|Sorgunun herhangi bir örneğini yürütmek için harcanan maksimum süre.|
|**Min Geçen Süre**|Sorgunun herhangi bir örneğini yürütmek için harcanan minimum süre.|
|**Avg Geçen Süre**|Sorgunun bir örneğini yürütmek için harcanan ortalama süre.|
