---
title: Katman etkileşimleri görünümü | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.tierinteraction
helpviewer_keywords:
- Tier Interactions view
ms.assetid: bb4fb21c-f3f7-473a-8b5e-442da4c2c445
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd60c855bacaf62beec47c9f977d0ab220ce7ca6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145540"
---
# <a name="tier-interactions-view"></a>Katman Etkileşimleri Görünümü
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Katman etkileşimi profili oluşturma, ile veritabanlarıyla iletişim kuran çok katmanlı uygulamaların işlevlerinde yürütme süreleri hakkında ek bilgiler sağlar [!INCLUDE[vstecado](../includes/vstecado-md.md)] . Veriler yalnızca zaman uyumlu işlev çağrıları için toplanır.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]  
  
  Etkileşimler görünümü, katman etkileşim verilerini iki bölme halinde görüntüler:  
  
- Ana bölme hiyerarşik bir ağacıdır. En üst düzey satır, bir sayfa veya işlemin veritabanı bağlantıları için toplanan verileri içerir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . Alt düğümler, üst öğenin veritabanı bağlantıları için toplanan verileri içerir.  
  
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
