---
title: 'Nasıl Kullanılır: Performans Verisi Dosya Adı Seçeneklerini Ayarlama | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cc42b63524a867c0893aa255180c740d03d4b5fe
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778771"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Nasıl yapılır: Performans veri dosyası adlandırma seçeneklerini ayarlama

Varsayılan olarak, bir profil oluşturma verisi kaydedersiniz (.* vsp*) dosyası aşağıdaki sözdizimi kullanarak:

*Yol\VSP-Dosya\YYMMDD(N)* **.vsp**

Performans oturumu için özellikler iletişim kutusunun **Genel** sayfasındaki herhangi bir adlandırma parametresini değiştirebilirsiniz.

|||
|-|-|
|*Yol*|Raporu içeren dizin. Varsayılan konum, çözüm klasörü veya kullanıcının projeleri ve çözümleri için varsayılan konumdur.|
|*VSP Dosyası*|Profil oluşturma veri dosyasının adı. Varsayılan ad, profilli çözümün veya yürütülebilir çözümün adıdır.|
|*YYMMDD*|Profil oluşturma verilerinin toplandığı yılı, ayı ve günü gösteren tarih damgası.|
|*(N)*|Birden fazla profil oluşturma veri dosyası varsa, parantezler arasında dosya adına artımlı bir sayı eklenir.|

## <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Performans oturumunun profil oluşturma veri dosyalarının adlandırma sözdizimini değiştirmek için

1. **Performans Gezgini'nde,** performans oturumunun adını sağ tıklatın ve ardından **Özellikler'i**tıklatın.

2. **Genel'i**tıklatın.

3. **Rapor**altında, aşağıdaki ayarlardan herhangi birini değiştirin:

    |||
    |-|-|
    |**Rapor konumu**|Profil oluşturma veri dosyalarını depolamak için bir dizin belirtin.|
    |**Rapor adı**|Dosyalar için bir temel ad belirtin.|
    |**Oturuma otomatik olarak yeni raporlar ekleme**|Veri dosyasını performans oturumuna otomatik olarak eklemek için onay kutusunu seçin.|
    |**Oluşturulan raporlara artış lı bir sayı ekle**|Aynı ada ait birden fazla dosya olduğunda dosya adına artış numarası eklemek için onay kutusunu seçin. Varolan bir dosyanın üzerine yazmak için onay kutusunu temizleyin.|
    |**Numara için zaman damgası kullanma**|Dosya adına tarih damgası eklemek için onay kutusunu seçin.|
