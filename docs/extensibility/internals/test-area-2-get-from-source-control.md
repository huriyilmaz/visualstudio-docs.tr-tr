---
title: 'Test alanı 2: kaynak denetiminden al | Microsoft Docs'
description: Bu test alanı, Al ile sürüm deposundan öğeleri almaya yönelik test çalışmalarını ele alır. Bu test çalışmaları, hem yerel hem de Web projelerine uygulanabilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2e16a515f0d307f2be1b2a2869c8de8b328e26ee
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158820"
---
# <a name="test-area-2-get-from-source-control"></a>Test Alanı 2: Kaynak Denetiminden Alma
Bu test alanı, Al komutu aracılığıyla sürüm deposundan öğeleri almaya yönelik test çalışmalarını ele alır. Bu test çalışmaları, hem yerel hem de Web projelerine uygulanabilir.

## <a name="command-menu-access"></a>Komut menüsü erişimi
 Aşağıdaki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamı menü yolları test durumlarında kullanılır.

##### <a name="get-latest-version"></a>En son sürümü Al:

- **Dosya**, **kaynak denetimi**, **en son sürümü Al**.

- **Dosya**, **en son sürümü Al**.

- Kısayol menüsü, **en son sürümü Al**.

- Al: **Dosya**, **kaynak denetimi**, **Get**.

## <a name="expected-behavior"></a>Beklenen davranış

##### <a name="get-latest-version"></a>En son sürümü Al:
 Sürüm deposundan öğenin en son sürümünü sessiz (Kullanıcı arabirimi) alma işlemini gerçekleştirir.

##### <a name="get"></a>Al:
 **Al** iletişim kutusunu görüntüler ve kullanıcının alınacak dosya kümesinde değişiklik yapmasına ve dosyaların nasıl alındığını etkileyen seçenekleri değiştirmesine izin verir.

## <a name="test-cases"></a>Test Çalışmaları

|Eylem|Test adımları|Doğrulanacak beklenen sonuçlar|
|------------|----------------|--------------------------------|
|Yerel olarak mevcut olmayan bir dosyanın en son sürümünü al|1. bir proje oluşturun.<br />2. projeye bir öğe ekleyin.<br />3. projeyi kaynak denetimi altına yerleştirin.<br />4. öğenin yerel kopyasını silin.<br />5. öğenin en son sürümünü alın (kısayol menüsü, **en son sürümü Al**).|Öğe dosyası yerel olarak alındı.|
|Yerel olarak mevcut olmayan bir dosya al|1. bir proje oluşturun.<br />2. projeye bir öğe ekleyin.<br />3. projeyi kaynak denetimi altına yerleştirin.<br />4. öğenin yerel kopyasını silin.<br />5. öğeyi (**Dosya**, **kaynak denetimi**, **Get** \<item> ) alın.|Öğe dosyası yerel olarak alındı.|
|Özel olarak kullanıma alınmış ve yerel olarak değiştirilen bir dosyayı alma|1. bir proje oluşturun.<br />2. projeye bir öğe ekleyin.<br />3. projeyi kaynak denetimi altına yerleştirin.<br />4. yalnızca proje öğesine göz atın.<br />5. Yerel kopyayı değiştirin.<br />6. öğenin en son sürümünü alın (**Dosya**, **en son sürümünü al** \<item> ). Bu adım başarılı olursa sonraki adımla devam edin.<br />7. uyarı iletişim kutusunda **Değiştir** düğmesine tıklayın.|**Adım 6 ' dan tekrar tekrar sonucu**`:`<br /><br /> Uyarı iletişim kutusu, dosyanın kullanıma alınmış olduğunu gösterir.<br /><br /> **7. adımda tekrar sonucu:**<br /><br /> Değiştirilen yerel dosya, sürüm deposundaki özgün sürümle değiştirilir.<br /><br /> Dosya okuma/yazma.|
|Kullanıma alınmış, paylaşılan ve yerel olarak değiştirilen dosyayı alma ve değiştirme|1. yeni bir proje oluşturun.<br />2. projeye bir öğe ekleyin.<br />3. projeyi kaynak denetimi altına yerleştirin.<br />4. proje öğesine paylaşılan olarak göz atın.<br />5. Yerel kopyayı değiştirin.<br />6. öğenin en son sürümünü alın (**Dosya**, **en son sürümünü al** \<item> ). Bu adım başarılı olursa sonraki adımla devam edin.<br />7. uyarı iletişim kutusunda **Değiştir** 'e tıklayın.|**6. adımdan elde edilen sonuç:**<br /><br /> Uyarı iletişim kutusu, dosyanın kullanıma alınmış olduğunu gösterir.<br /><br /> **Adım 7:**<br /><br /> Değiştirilen yerel dosya, sürüm deposundaki özgün sürümle değiştirilir.<br /><br /> Dosya okuma/yazma.|
|Yerel olarak var olan bir dosyayı, sürüm deposundaki en son sürümle aynı şekilde alın|1. yeni bir proje oluşturun.<br />2. projeye bir öğe ekleyin.<br />3. projeyi kaynak denetimi altına yerleştirin.<br />4. öğeyi (**Dosya**, **kaynak denetimi**, **Get** \<item> ) alın.|Yerel dosya değiştirilmez.|
|Bir projeyle bir çözüm alın|1. bir projeyle bir çözüm oluşturun.<br />2. çözümü kaynak denetimi altına yerleştirin.<br />3. tüm proje dosyalarını yerel olarak silin.<br />4. çözümü (**Dosya**, **kaynak denetimi**, **Get**) alın.|Silinen tüm dosyalar yerel olarak geri yüklenir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
