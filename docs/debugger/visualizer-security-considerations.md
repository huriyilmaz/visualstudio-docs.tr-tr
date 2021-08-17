---
title: Görselleştirici Güvenlik Konuları | Microsoft Docs
description: Hata ayıklayıcısı için Visual Studio bir görselleştiricinin tam güven ile çalışması gerekir. Siz kendi güvenlik tehditlerinizi yazarken olası güvenlik tehditlerine dikkat ve uygun önlemleri alın.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4bfe2884e4e6fc8335467bdd8b37012e33ba1867c68a64a20c87b120d0aba46c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121418564"
---
# <a name="visualizer-security-considerations"></a>Görselleştirici Güvenlik Konuları
Görselleştirici yazmak olası güvenlik tehditlerini içerir. Şu anda bu olası tehditler için bilinen bir açık yoktur, ancak geliştiricilerin gelecekte ortaya çıkarılara karşı koruma için bu tehditlerin farkında olması ve burada açıklandığı gibi uygun güvenlik önlemlerini almaları gerekir.

 Hata ayıklayıcı görselleştiricileri, kısmi bir güven uygulaması tarafından izin verilenden daha fazla ayrıcalık gerektirir. Kısmi güven ile kodda durdurulurken görselleştiriciler yüklenmez. Görselleştirici kullanarak hata ayıklamak için kodu tam güvenle çalıştırmalısiniz.

## <a name="possible-malicious-debuggee-component"></a>Olası Kötü Amaçlı Hata Ayıklayıcı Bileşeni
 Görselleştiriciler en az iki sınıftan oluşur: biri hata ayıklayıcı tarafında, biri hata ayıklayıcısı tarafında. Görselleştiriciler genellikle özel dizinlere konulan ayrı derlemelere dağıtılır, ancak bunlar hata ayıklayıcıdan da yüklenebilir. Bu durum oluştuğunda, hata ayıklayıcı kodu hata ayıklayıcıdan alır ve tam güven ile hata ayıklayıcısı içinde çalıştırır.

 Hata ayıklayıcıya tam olarak güveni sağlanmazsa hata ayıklayıcı tarafı kodun tam güven ile çalıştırılası sorunlu hale gelir. Görselleştirici hata ayıklayıcıdan hata ayıklayıcısına kısmi bir güven derlemesi yüklemeye çalışırsa, Visual Studio görselleştiriciyi sonlandırılır.

 Ancak yine de küçük bir güvenlik açığı vardır. Hata ayıklayıcısı tarafı, başka bir kaynaktan yüklenen (hata ayıklayıcı değil) bir hata ayıklayıcı tarafıyla ilişkilendirilebiliyor. Daha sonra hata ayıklayıcı tarafı, güvenilir hata ayıklayıcı tarafının kendi adına eylemler gerçekleştirmesini söyler. Güvenilen hata ayıklayıcı tarafı sınıfı bir "bu dosyayı sil" mekanizmasını ortaya çıkarırsa, kullanıcı görselleştiricisini çağıran kısmi güven hata ayıklayıcısı bu mekanizmayı çağırabilirsiniz.

 Bu güvenlik açığını azaltmak için görselleştiricinizin ortaya çıkarması gereken arabirimlere dikkat etmek gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Görselleştirici Mimarisi](../debugger/visualizer-architecture.md)
- [Nasıl Yapılır: Görselleştirici Yazma](create-custom-visualizers-of-data.md)
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
- [Hata Ayıklayıcıda Verileri Görüntüleme](../debugger/viewing-data-in-the-debugger.md)