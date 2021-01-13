---
title: Görselleştirici güvenlik konuları | Microsoft Docs
description: Visual Studio hata ayıklayıcısı için Görselleştirici tam güvenle çalıştırılmalıdır. Siz yazarken, olası güvenlik tehditlerine karşı haberdar olun ve uygun önlemleri alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, security
- security [Visual Studio], visualizers
ms.assetid: cdd86bd5-b729-409b-a7c6-374efa091eb1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2db18a1443b0c4faaa288a887a22d935d243f678
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149748"
---
# <a name="visualizer-security-considerations"></a>Görselleştirici Güvenlik Konuları
Görselleştiricisi yazmak olası güvenlik tehditlerini içerir. Bu olası tehditler için şu anda bilinen bir Exploit yok, ancak geliştiriciler bunların farkında olmalıdır ve gelecekte aşağıda açıklandığı gibi uygun güvenlik önlemleri almalıdır.

 Hata ayıklayıcı Görselleştiriciler kısmi güven uygulaması tarafından izin verilenden daha fazla ayrıcalık gerektiriyor. Kısmi güvenle kodda durdurulduğunda, Görselleştiriciler yüklenmez. Görselleştirici kullanarak hata ayıklamak için, kodu tam güvenle çalıştırmanız gerekir.

## <a name="possible-malicious-debuggee-component"></a>Olası kötü amaçlı hata ayıklanan bileşen
 Görselleştiriciler en az iki sınıftan oluşur: biri hata ayıklayıcı tarafında ve hata ayıklanan tarafta bir tane. Görselleştiriciler, genellikle özel dizinlere yerleştirilen ayrı derlemelerde dağıtılır, ancak hata ayıklanan içinden de yüklenebilir. Bu durum oluştuğunda, hata ayıklayıcı kodu hata ayıklanan dışına alır ve tam güvenle hata ayıklayıcı içinde çalıştırır.

 Hata ayıklanan yan yana kodu tam güvenle çalıştırmak, hata ayıklama tam güvenilir olmadığında sorunlu hale gelir. Bir Görselleştirici hata ayıklayıcıya ayıklanan bir kısmi güven derlemesini yüklemeye çalışırsa, Visual Studio Görselleştiriciyi sonlandırır.

 Ancak, ikincil bir güvenlik açığı hala mevcuttur. Hata ayıklanan tarafı, başka bir kaynaktan yüklenmiş (hata ayıklanan) bir hata ayıklayıcı tarafı ile ilişkilendirilebilmesi. Hata ayıklanan kenar daha sonra bu güvenilir hata ayıklayıcı tarafında, onun adına eylem gerçekleştirmesini söyleyebilir. Güvenilir hata ayıklayıcı tarafı sınıfı "bu dosyayı sil" mekanizmasını kullanıma sunarsa, örneğin kısmi güven hata ayıklanan Kullanıcı Görselleştirici çağırdığında bu mekanizmayı çağırabilir.

 Bu güvenlik açığını azaltmak için Görselleştiricinizi açığa çıkarması gereken arabirimlerin en az olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Görselleştiricisi mimarisi](../debugger/visualizer-architecture.md)
- [Nasıl Yapılır: Görselleştirici Yazma](create-custom-visualizers-of-data.md)
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
- [Hata Ayıklayıcıda Verileri Görüntüleme](../debugger/viewing-data-in-the-debugger.md)