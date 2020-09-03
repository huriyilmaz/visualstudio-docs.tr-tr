---
title: 'Nasıl yapılır: performans veri dosyası adı seçeneklerini ayarlama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 71ac053a24b3f765a58fc050ceec84115e1a4e3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548401"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Nasıl yapılır: performans veri dosyası adı seçeneklerini ayarlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Varsayılan olarak, aşağıdaki sözdizimini kullanarak bir profil oluşturma verileri (. vsp) dosyası kaydedersiniz:  
  
 *Yol\vsp-file\ydd (N)* **. vsp**  
  
 Performans oturumunun Özellikler iletişim kutusunun Genel sayfasında herhangi bir adlandırma parametresini değiştirebilirsiniz.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
|Söz dizimi öğesi|Açıklama|  
|-|-|  
|*Yol*|Raporu içeren dizin. Varsayılan konum, çözüm klasörüdür veya kullanıcının projeleri ve çözümleri için varsayılan konumdur.|  
|*VSP dosyası*|Profil oluşturma veri dosyasının adı. Varsayılan ad, profil oluşturulan çözümün veya yürütülebilir dosyanın adıdır.|  
|*YYAAGG*|Profil oluşturma verilerinin toplandığı yılı, ayı ve günü gösteren bir tarih damgası.|  
|*No*|Birden fazla profil oluşturma veri dosyası varsa, parantez arasında dosya adına artan bir sayı eklenir.|  
  
### <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Bir performans oturumunun profil oluşturma veri dosyalarının adlandırma sözdizimini değiştirmek için  
  
1. **Performans Gezgini**, performans oturumunun adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
2. **Genel**' e tıklayın.  
  
3. **Rapor**' ın altında, aşağıdaki ayarlardan birini değiştirin:  
  
    |Ad|Açıklama|  
    |-|-|  
    |**Rapor konumu**|Profil oluşturma veri dosyalarını depolamak için bir dizin belirtin.|  
    |**Rapor adı**|Dosyalar için bir temel ad belirtin.|  
    |**Oturuma otomatik olarak yeni raporlar ekleyin**|Veri dosyasını otomatik olarak performans oturumuna eklemek için onay kutusunu işaretleyin.|  
    |**Oluşturulan raporlara artan bir sayı Ekle**|Aynı ada sahip birden fazla dosya varsa dosya adına bir artan sayı eklemek için onay kutusunu işaretleyin. Varolan bir dosyanın üzerine yazmak için onay kutusunu temizleyin.|  
    |**Numara için zaman damgası kullanın**|Dosya adına bir dateStamp eklemek için onay kutusunu işaretleyin.|
