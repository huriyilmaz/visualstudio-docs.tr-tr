---
title: Katman etkileşimleri görünümü | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74778147"
---
# <a name="tier-interactions-view"></a>Katman Etkileşimleri Görünümü

Katman etkileşimi profili oluşturma, ile veritabanlarıyla iletişim kuran çok katmanlı uygulamaların işlevlerinde yürütme süreleri hakkında ek bilgiler sağlar [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] . Veriler yalnızca zaman uyumlu işlev çağrıları için toplanır.

**Gereksinimler**

- Visual Studio Enterprise

Etkileşimler görünümü, katman etkileşim verilerini iki bölme halinde görüntüler:

- Ana bölme hiyerarşik bir ağacıdır. En üst düzey satır, bir sayfa veya işlemin veritabanı bağlantıları için toplanan verileri içerir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] . Alt düğümler, üst öğenin veritabanı bağlantıları için toplanan verileri içerir.

- Ana bölmedeki bir veritabanı çağrısı düğümüne tıkladığınızda, veritabanı çağrısının örneğine ilişkin veriler Ayrıntılar bölmesinde görüntülenir.

  Süre, milisaniye sayısı veya CPU saat işaretleri sayısı olarak görüntülenir. Görüntülenecek zaman birimini değiştirmek için, **Araçlar** menüsüne tıklayın, **Seçenekler**' e tıklayın ve ardından **zaman değerlerini göster** seçeneklerinden birini belirleyin.

## <a name="master-pane"></a>Ana bölme

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|-En üst düzey bir satır için, profili oluşturulmuş işlemin veya Web sayfasının adı.<br />-Veritabanı bağlantı satırı için, veritabanını barındıran sunucunun adı.|
|**Veritabanı**|Veritabanının adı (yalnızca veritabanı bağlantı satırları).|
|**Biriktirme**|İşlem, Web sayfası veya veritabanı bağlantısı tarafından oluşturulan isteklerin toplam sayısı.|
|**Geçen toplam süre**|İşlem, Web sayfası veya veritabanı bağlantısından herhangi bir isteği yürütmek için harcanan toplam süre.|
|**Geçen en uzun süre**|İşlem, Web sayfası veya veritabanı bağlantısından herhangi bir isteği yürütmek için harcanan en uzun süre.|
|**Geçen en az süre**|İşlem, Web sayfası veya veritabanı bağlantısından herhangi bir isteği yürütmek için harcanan en kısa süre.|
|**Ortalama geçen süre**|İşlemin, Web sayfasının veya veritabanı bağlantısının bir isteğini yürütmek için harcanan ortalama süre.|

## <a name="database-connection-details-pane"></a>Veritabanı bağlantısı ayrıntıları bölmesi

|Sütun|Açıklama|
|------------|-----------------|
|**Komut metni**|İsteğin SQL sorgusu.|
|**Sorgu sayısı**|Sorgunun kaç kez çalıştırıldığı.|
|**Geçen toplam süre**|Sorgunun örneklerini yürütmek için harcanan toplam süre.|
|**Geçen en uzun süre**|Sorgunun herhangi bir örneğini yürütmek için harcanan en uzun süre.|
|**Geçen en az süre**|Sorgunun herhangi bir örneğini yürütmek için harcanan en kısa süre.|
|**Ortalama geçen süre**|Sorgunun bir örneğini yürütmek için harcanan ortalama süre.|
