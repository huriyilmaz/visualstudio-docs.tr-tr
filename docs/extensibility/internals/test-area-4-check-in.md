---
title: 'Test Alanı 4: Giriş | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2386a217de228c5c47b467e6e083d978702927f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704569"
---
# <a name="test-area-4-check-in"></a>Test Alanı 4: İade Etme
Bu kaynak denetimi eklentisi test alanı, Iade **Et** komutu aracılığıyla güncelleştirilmiş öğelerin sürüm deposuna gönderilmesini kapsar.

## <a name="command-menu-access"></a>Komut Menüsü ne erişim
 Test [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] servis örneklerinde aşağıdaki tümleşik geliştirme ortamı menü yolları kullanılır.

##### <a name="check-in"></a>Teslim etme:
 **Dosya**, **Kaynak Denetimi**, **Giriş**

 **Dosya**, **Giriş**

 Kısayol menüsü, **Giriş Yapın**.

## <a name="common-expected-behavior"></a>Ortak Beklenen Davranış

- Kaynak denetimi altındaki bir çözüme veya projeye eklenen projeler ve **dosyalar, İade et** iletişim kutusunda ve **Bekleyen Denetimler** penceresinde görünür.

- İadeden sonra, eklenen öğeler kaynak denetiminde görünür.

- İadeden sonra, güncelleştirilmiş öğeler mağazada düzgün bir şekilde sürülür.

## <a name="test-cases"></a>Test Çalışmaları
 Checkin test alanı için özel test çalışmaları aşağıda veda edilebistir.

### <a name="case-4a-modified-items"></a>Örnek 4a: Değiştirilmiş öğeler
 Değiştirilen kaynak denetimi altındaki bir dosyayı güncelleştirmek için iade eylemini kullanma açıklar.

|Eylem|Test Adımları|Doğrulaması Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Kullanıma alınmış bir metin dosyasini değiştirin, yalnızca dosyayı iade edin ( Giriş yap iletişim**kutusunu)**|1. Metin dosyasıyla yeni bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Metin dosyasını kontrol edin ve değiştirin.<br />4. Giriş yap iletişim kutusu üzerinden giriş yap (**Dosya**, **Kaynak Denetimi**, Giriş **Yap**).|Ortak Beklenen Davranış.|
|Kullanıma alınmış bir metin dosyasini değiştirme, yalnızca dosyayı iade et **(Bekleyen İadeler** penceresi)|1. Metin dosyasıyla yeni bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Metin dosyasını kontrol edin ve değiştirin.<br />4. Bekleyen İadeler penceresinden **check-in** edin.|Ortak Beklenen Davranış.|

### <a name="case-4b-adding-files"></a>Örnek 4b: Dosya ekleme
 Bir projeye veya bir öğeye bir çözüme dosya eklerken, proje veya çözüm de değişmesi gerekir. Bu nedenle üst dosya da kullanıma alınmalıdır ve eklemeyi tamamlamak için iade edilmesi gerekir.

|Eylem|Test Adımları|Doğrulaması Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Metin dosyası ekleyin ve her şeyi iade edin (Giriş Yap iletişim kutusunu**işaretleyin)**|1. Yeni bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Projeye bir metin dosyası ekleyin.<br />4. İstenirse projeden çıkış yap'ı kabul edin.<br />5. **Çözüm Gezgini'nde**çözümü seçin.<br />6. **Giriş Yap** iletişim kutusundan giriş yapın.|Ortak Beklenen Davranış.|
|Metin dosyası ekleyin ve her şeyi iade edin **(Bekleyen İadeler** penceresi)|1. Yeni bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Projeye bir metin dosyası ekleyin.<br />4. İstenirse projeden çıkış yap'ı kabul edin.<br />5. Bekleyen İadeler penceresinden çözümü iade **edin.**|Ortak Beklenen Davranış|

### <a name="case-4c-adding-projects"></a>Örnek 4c: Proje ekleme
 Bir çözüme proje eklerken, çözüm de değiştirilmelidir. Bu nedenle çözüm dosyası da kullanıma alınmalıdır ve eklemeyi tamamlamak için iade edilmesi gerekir.

|Eylem|Test Adımları|Doğrulaması Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Kaynak denetimi altındaki boş bir çözüme proje ekleme **(Giriş Kutusu'nı Iade Et)**|1. Boş bir çözüm oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Yeni bir proje ekleyin.<br />4. İstenirse çözümden çıkış kabul edin.<br />5. **Giriş Yap** iletişim kutusundan giriş yapın.|Ortak Beklenen Davranış.|
|Kaynak denetimi altındaki boş bir çözüme proje ekleme **(Bekleyen İadeler** penceresi)|1. Boş bir çözüm oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Yeni bir proje ekleyin.<br />4. İstenirse çözümden çıkış kabul edin.<br />5. Bekleyen İadeler penceresinden çözümü iade **edin.**|Ortak Beklenen Davranış.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
