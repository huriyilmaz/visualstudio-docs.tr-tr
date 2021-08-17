---
title: 'Test Alanı 7: Paylaşım | Microsoft Docs'
description: Bu kaynak denetimi test alanı, kaynak denetimi eklentiniz için Paylaş komutunu kullanarak Visual Studio paylaşmayı kapsar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 23b5564470551b1732e57e4cf07cbd191c069d21afd6ac1f0b563f596c852fcd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121431779"
---
# <a name="test-area-7-share"></a>Test Alanı 7: Paylaş
Bu test alanı, Paylaş komutu aracılığıyla konumlar arasında öğe **paylaşımını** kapsar.

 Hhare işlemi, bir kaynak denetim dosyası hiyerarşisi içindeki iki veya daha fazla konum arasında dosya ve klasör öğelerinin görünür bir şekilde çoğaltılmasıdır. Yineleme sunucuda gerçekten oluşmaz, ancak kullanıcı aynı dosyayı belirtilen iki veya daha fazla konumda görebilir. Paylaşılan öğelerden herhangi biri üzerinde her değişiklik yapıldı mı, bu değişiklikler diğer tüm paylaşılan konumlarda görünür.

 Klasörlerde paylaşım, içinde kaynak denetimi altında en az bir dosya olan bir klasör seçmenize yarar. Paylaşım komutu aşağıdaki koşullar altında devre dışı bırakılır:

- Seçilen klasör boş bir klasörse.

- Gerçek bir klasör varsa ancak kaynak denetim dosyası içeriyorsa.

- Kaynak denetimi altındaki dosyaların içinde olup olmadığı, sanal bir klasör varsa.

- Uzak Site Web projesi varsa.

## <a name="command-menu-access"></a>Komut Menüsü Erişimi
 Aşağıdaki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı menü yolları test çalışmalarında kullanılır.

 Paylaşım: **Dosya** -> **Kaynağı Denetim** -> **Paylaşımı.**

## <a name="expected-behavior"></a>Beklenen Davranış

- Paylaşılan dosya paylaşılan konumda görünür.

- Kaynak denetimi sürüm deposu geçmişini görüntülemek, dosyalarda paylaşım olduğunu gösterir.

- Paylaşılan bir dosyayı düzenlemek, dosyanın her iki konumunu da düzenler.

## <a name="test-cases"></a>Test Çalışmaları
 Aşağıda, Share test alanı için belirli test testleri yer almaktadır.

|Eylem|Test Adımları|Doğrulandı Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Kaynak denetimi altındaki bir yüklenen projeden başka bir yüklenen projeyle dosya paylaşma|1. Yeni bir proje oluşturun.<br />2. Çözüme ikinci bir proje ekleyin.<br />3. İkinci projede ilk projede yer alan bir adla bir dosya oluşturun.<br />4. Çözümü kaynak denetimine ekleyin.<br />5. İlk projeyi seçin.<br />6. Paylaş **iletişim** kutusunu açın (**Dosya Kaynağı**  ->  **Denetim**  ->  **Paylaşımı**).<br />7. dosyayı ikinci projeden ilk projeyle paylaşın.<br />8. **İstendiğinde Check Out** 'i kabul edin.|Ortak Beklenen Davranış.|
|Bir projeden diğerine dosya paylaşma|1. Yeni bir proje oluşturun.<br />2. Kaynak denetimine ekleyin.<br />3. Çözümü kapatın.<br />4. İkinci bir proje (yeni çözüm) oluşturun.<br />5. Çözümü kaynak denetimine ekleyin.<br />6. Projeyi seçin.<br />7. Paylaş iletişim **kutusunu** açın (**Dosya Kaynağı**  ->  **Denetim**  ->  **Paylaşımı**).<br />8. Daha önce eklenen projeden açık projeye bir dosya paylaşın.<br />9. **İstendiğinde Check Out** 'i kabul edin.|Ortak Beklenen Davranış.|
|Kaynak denetiminden projenin parçası değil, o anda yüklü olan projeyle dosya paylaşma|1. Yeni bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Kaynak denetimine projenin veya çözümün parçası olan bir dosya ekleyin.<br />4. Projeyi seçin ve Paylaş iletişim **kutusunu** açın (**Dosya Kaynağı**  ->  **Denetim**  ->  **Paylaşımı**).<br />5. Paylaş iletişim kutusunda **geçerli proje** veya çözüm içinde mevcut olmayan bir dosyayı seçin ve paylaşın.<br />6. **İstendiğinde Check Out** 'i kabul edin.|Kaynak denetim deposu bir Get işlemi gerçekleştirdi, bu nedenle dosya artık projenin yerel bir yerinde.|
|Aynı proje içindeki dosyaları farklı bir klasöre paylaşma|1. Araçlar **Seçenekleri Kaynak Denetimi'ne** **otomatik olarak** göz  ->    ->  **at'ı seçin.**<br />2. Yeni bir proje oluşturun ve bunu kaynak denetimine ekleyin.<br />3. Projeye bir klasör ekleyin.<br />4. Klasöre bir dosya ekleyin ve klasörünü iade edin.<br />5. Klasörü seçin.<br />6. Paylaş **iletişim** kutusunu açın (**Dosya Kaynağı**  ->  **Denetim**  ->  **Paylaşımı**).<br />7. Dosyayı seçili klasöre paylaşın.|Ortak Beklenen Davranış.<br /><br /> Klasör, paylaşım için kullanılmadan önce içinde bir dosyayla iade edilmelidir.|
|Yüklenen dosyada klasör paylaşma — Project|1. Yeni bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Projeyi seçin.<br />4. Paylaş iletişim **kutusunu** açın (**Dosya Kaynağı**  ->  **Denetim**  ->  **Paylaşımı**).<br />5. Bir klasör seçin.<br />6. Klasörü projede tekrar tekrar paylaşın.|Ortak Beklenen Davranış.|
|Bir projeden diğerine birkaç dosya paylaşma|1. Içinde birkaç dosya olan yeni bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Çözümü kapatın.<br />4. Yeni bir çözümde yeni bir proje oluşturun.<br />5. Çözümü kaynak denetimine ekleyin.<br />6. Projeyi seçin.<br />7. Paylaş iletişim **kutusunu** açın (**Dosya Kaynağı**  ->  **Denetim**  ->  **Paylaşımı**).<br />8. Önceden oluşturulmuş olan projeden açık olan projeyle birkaç dosya paylaşın.|Ortak Beklenen Davranış.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
