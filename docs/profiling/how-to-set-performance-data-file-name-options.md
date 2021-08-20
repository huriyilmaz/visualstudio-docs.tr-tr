---
title: Performans verisi dosya adı seçeneklerini ayarla | Microsoft Docs
description: Performans oturumunun Özellikler iletişim kutusunun Genel sayfasında herhangi bir adlandırma parametresini nasıl değiştirebileceğinizi öğrenin.
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 57c02081d31aa90e4b3c4c2415d515cf94d80aea
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150293"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Nasıl yapılır: Performans veri dosyası adlandırma seçeneklerini ayarlama

Varsayılan olarak, profil oluşturma verilerini (.*VSP*) dosyası aşağıdaki sözdizimini kullanarak:

*Yol\vsp-file\ydd (N)* **. vsp**

Performans oturumunun Özellikler iletişim kutusunun **genel** sayfasında herhangi bir adlandırma parametresini değiştirebilirsiniz.

|Parametre|Açıklama|
|-|-|
|*Yol*|Raporu içeren dizin. Varsayılan konum, çözüm klasörüdür veya kullanıcının projeleri ve çözümleri için varsayılan konumdur.|
|*VSP dosyası*|Profil oluşturma veri dosyasının adı. Varsayılan ad, profil oluşturulan çözümün veya yürütülebilir dosyanın adıdır.|
|*YYAAGG*|Profil oluşturma verilerinin toplandığı yılı, ayı ve günü gösteren bir tarih damgası.|
|*No*|Birden fazla profil oluşturma veri dosyası varsa, parantez arasında dosya adına artan bir sayı eklenir.|

## <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Bir performans oturumunun profil oluşturma veri dosyalarının adlandırma sözdizimini değiştirmek için

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
