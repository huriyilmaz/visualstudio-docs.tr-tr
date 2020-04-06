---
title: 'Test Alanı 2: Kaynak Kontrolünden Alın | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c213e2774730596db8b8e4f2d0691472495222e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704598"
---
# <a name="test-area-2-get-from-source-control"></a>Test Alanı 2: Kaynak Denetiminden Alma
Bu test alanı, Get komutu aracılığıyla sürüm deposundan öğeleri almak için test denemelerini kapsar. Bu test çalışmaları hem yerel hem de Web projelerine uygulanabilir.

## <a name="command-menu-access"></a>Komut Menüsü ne erişim
 Test [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] servis örneklerinde aşağıdaki tümleşik geliştirme ortamı menü yolları kullanılır.

##### <a name="get-latest-version"></a>En Son Sürümü Alın:

- **Dosya**, **Kaynak Denetimi**, En Son **Sürümü Alın**.

- **Dosya**, **En Son Sürümü Alın**.

- Kısayol menüsü, **En Son Sürümü Alın**.

- Get: **Dosya**, **Kaynak Denetimi**, **Alın**.

## <a name="expected-behavior"></a>Beklenen Davranış

##### <a name="get-latest-version"></a>En Son Sürümü Alın:
 Öğenin en son sürümünü sürüm deposundan sessiz (hiçbir UI) alma gerçekleştirir.

##### <a name="get"></a>Al:
 **Al** iletişim kutusunu görüntüler ve kullanıcının dosya kümesinde alınabilecek değişiklikler yapmasına ve dosyaların nasıl alındığını etkileyen seçenekleri değiştirmesine olanak tanır.

## <a name="test-cases"></a>Test Çalışmaları

|Eylem|Test Adımları|Doğrulaması Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Yerel olarak var olmayan bir dosyanın En Son Sürümünü Alın|1. Bir proje oluşturun.<br />2. Projeye bir öğe ekleyin.<br />3. Projeyi kaynak kontrolü altına koyun.<br />4. Öğenin yerel kopyasını silin.<br />5. Öğenin En Son Sürümünü Alın (Kısayol Menüsü, **En Son Sürümü Alın**).|Öğe dosyası yerel olarak alınır.|
|Yerel olarak var olmayan bir dosya yı alma|1. Bir proje oluşturun.<br />2. Projeye bir öğe ekleyin.<br />3. Projeyi kaynak kontrolü altına koyun.<br />4. Öğenin yerel kopyasını silin.<br />5. Öğeyi alın **(Dosya**, **Kaynak Denetimi**, öğe yi **> alın).** \<|Öğe dosyası yerel olarak alınır.|
|Yalnızca kullanıma alınmış ve yerel olarak değiştirilmiş bir dosya alma|1. Bir proje oluşturun.<br />2. Projeye bir öğe ekleyin.<br />3. Projeyi kaynak kontrolü altına koyun.<br />4. Proje öğesine yalnızca göz atın.<br />5. Yerel kopyayı değiştirin.<br />6. Öğenin En Son Sürümünü Alın **(Dosya**, **öğenin** \<en son sürümünü alın>). Bu adım başarılı olursa, bir sonraki adıma devam edin.<br />7. Uyarı iletişim kutusunda **değiştir** düğmesini tıklatın.|**Adım 6'dan Sonuç**`:`<br /><br /> Uyarı iletişim kutusu, dosyanın kullanıma açılmış olduğunu gösterir.<br /><br /> **7. Adımdan Sonuç:**<br /><br /> Değiştirilen yerel dosya, sürüm deposundan özgün sürümle değiştirilir.<br /><br /> Dosya okunur/yazılır.|
|Kullanıma alındı, paylaşıldı ve yerel olarak değiştirildi dosyayı alın ve değiştirin|1. Yeni bir proje oluşturun.<br />2. Projeye bir öğe ekleyin.<br />3. Projeyi kaynak kontrolü altına koyun.<br />4. Paylaşılan proje öğesine göz atın.<br />5. Yerel kopyayı değiştirin.<br />6. Öğenin En Son Sürümünü Alın **(Dosya**, **öğenin** \<en son sürümünü alın>). Bu adım başarılı olursa, bir sonraki adıma devam edin.<br />7. Uyarı iletişim kutusunda **Değiştir'i** tıklatın.|**Adım 6'dan elde edilen sonuç:**<br /><br /> Uyarı iletişim kutusu, dosyanın kullanıma açılmış olduğunu gösterir.<br /><br /> **Adım 7'den elde edilen sonuç:**<br /><br /> Değiştirilen yerel dosya, sürüm deposundan özgün sürümle değiştirilir.<br /><br /> Dosya okunur/yazılır.|
|Sürüm deposundaki en son sürümle aynı şekilde yerel olarak var olan bir dosyayı alın|1. Yeni bir proje oluşturun.<br />2. Projeye bir öğe ekleyin.<br />3. Projeyi kaynak kontrolü altına koyun.<br />4. Öğeyi alın **(Dosya**, **Kaynak Denetimi**, Öğe yi **al** \<>).|Yerel dosya değişmedi.|
|Tek bir projeyle çözüm elde edin|1. Tek bir proje ile çözüm oluşturun.<br />2. Çözümü kaynak kontrolü altına yerleştirin.<br />3. Tüm proje dosyalarını yerel olarak silin.<br />4. Çözüm alın (**Dosya**, **Kaynak Kontrol**, **Get**).|Silinen tüm dosyalar yerel olarak geri yüklenir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
