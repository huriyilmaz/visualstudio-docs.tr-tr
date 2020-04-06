---
title: 'Test Alanı 7: Paylaş | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd4c48e94015d95f5e56d465cdbf98562108d3b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704400"
---
# <a name="test-area-7-share"></a>Test Alanı 7: Paylaşma
Bu test alanı, **Paylaş** komutu aracılığıyla öğelerin konumlar arasında paylaşılmasını kapsar.

 Hhare işlemi, kaynak denetim dosyası hiyerarşisi içinde iki veya daha fazla konum arasında dosya ve klasör öğelerinin görünürde çoğaltılmasıdır. Yineleme gerçekten sunucuda oluşmaz, ancak kullanıcı aynı dosyayı iki veya daha fazla belirtilen konumlarda görür. Paylaşılan öğelerden herhangi birinde değişiklik yapıldığında, bu değişiklikler diğer tüm paylaşılan konumlarda görünür.

 Klasörlere paylaşmak, içinde kaynak denetimi altında en az bir dosya bulunan bir klasör seçerseniz çalışır. Paylaşım komutu aşağıdaki koşullar altında devre dışı bırakılır:

- Seçili klasör boş bir klasörse.

- Gerçek bir klasör varsa, ancak kaynak denetim dosyaları içeriyorsa.

- Sanal bir klasör varsa, kaynak denetimi altındaki dosyaların içinde olup olmadığı.

- Uzak Site Web projesi varsa.

## <a name="command-menu-access"></a>Komut Menüsü ne erişim
 Test [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] servis örneklerinde aşağıdaki tümleşik geliştirme ortamı menü yolları kullanılır.

 Paylaş: **Dosya**->**Kaynak Denetim**->**Payı**.

## <a name="expected-behavior"></a>Beklenen Davranış

- Paylaşılan dosya paylaşılan konumda görünür.

- Kaynak denetimi sürümü deposu nun geçmişi görüntülenmek, dosyanın(lar) paylaşıldığını gösterir.

- Paylaşılan dosyayı düzenlemek, dosyanın her iki konumunu da düzenler.

## <a name="test-cases"></a>Test Çalışmaları
 Aşağıda, Share test alanı için özel test çalışmaları vereme leri yer almaktadır.

|Eylem|Test Adımları|Doğrulaması Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Kaynak denetimi altında yüklü bir projeden yüklenen bir projeden başka bir yüklenen projeye dosya paylaşma|1. Yeni bir proje oluşturun.<br />2. Çözüme ikinci bir proje ekleyin.<br />3. İkinci projede ilk projede olmayan bir adiçeren bir dosya oluşturun.<br />4. Çözümü kaynak denetimine ekleyin.<br />5. İlk projeyi seçin.<br />6. **Paylaş** iletişim kutusunu aç (**Dosya** -> **Kaynak Denetimi** -> **Paylaş**).<br />7. İkinci projeden ilk projeye dosyayı paylaşın.<br />8. İstenirse **Kullanıma Hemen Kabul** Et.|Ortak Beklenen Davranış.|
|Bir projeden diğerine dosya paylaşma|1. Yeni bir proje oluşturun.<br />2. Kaynak denetimine ekleyin.<br />3. Çözümü kapatın.<br />4. İkinci bir proje oluşturun (yeni çözüm.)<br />5. Çözümü kaynak denetimine ekleyin.<br />6. Projeyi seçin.<br />7. **Paylaş** iletişim kutusunu açın (**Dosya** -> **Kaynak Denetimi** -> **Paylaş**).<br />8. Daha önce eklenen projeden bir dosyayı açık projeye paylaşın.<br />9. İstenirse **Kullanıma Hemen Kabul** Et.|Ortak Beklenen Davranış.|
|Kaynak denetiminden projenin parçası olmayan bir dosyayı şu anda yüklenen projeye paylaşma|1. Yeni bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Projenin veya çözümün parçası olmayan kaynak denetimine bir dosya ekleyin.<br />4. Projeyi seçin ve **Paylaş** iletişim kutusunu açın (**Dosya** -> **Kaynak Denetimi** -> **Paylaş**).<br />5. Geçerli proje veya çözüm içinde bulunmayan **Paylaş** iletişim kutusunda bir dosya seçin ve paylaşın.<br />6. İstenirse **Kullanıma Hemen Kabul** Et.|Kaynak denetim deposu Get gerçekleştirmiştir, bu nedenle dosya artık projenin yerel konumundadır.|
|Aynı projedeki dosyaları farklı bir klasöre paylaşma|1. **Araçlar** -> **Seçenekleri** -> **Kaynak Denetimi'nde**otomatik olarak **kullanıma çekin'i** seçin.<br />2. Yeni bir proje oluşturun ve kaynak denetimine ekleyin.<br />3. Projeye bir klasör ekleyin.<br />4. Klasöre bir dosya ekleyin ve klasörü iade edin.<br />5. Klasörü seçin.<br />6. **Paylaş** iletişim kutusunu aç (**Dosya** -> **Kaynak Denetimi** -> **Paylaş**).<br />7. Dosyayı seçili klasöre paylaşın.|Ortak Beklenen Davranış.<br /><br /> Klasör, paylaşım için kullanılabilmesi için içinde bir dosya ile iade edilmelidir.|
|Yüklenen Projeye klasör ü paylaşın — Yinelemeli|1. Yeni bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Projeyi seçin.<br />4. **Paylaş** iletişim kutusunu açın (**Dosya** -> **Kaynak Denetimi** -> **Paylaş**).<br />5. Bir klasör seçin.<br />6. Klasörü projeye özyinelemeli olarak paylaşın.|Ortak Beklenen Davranış.|
|Bir projeden diğerine birden fazla dosya paylaşma|1. Içinde birkaç dosya bulunan yeni bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Çözümü kapatın.<br />4. Yeni bir çözüm de yeni bir proje oluşturun.<br />5. Çözümü kaynak denetimine ekleyin.<br />6. Projeyi seçin.<br />7. **Paylaş** iletişim kutusunu açın (**Dosya** -> **Kaynak Denetimi** -> **Paylaş**).<br />8. Daha önce oluşturulmuş projeden şu anda açık olan projeye birkaç dosya paylaşın.|Ortak Beklenen Davranış.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
