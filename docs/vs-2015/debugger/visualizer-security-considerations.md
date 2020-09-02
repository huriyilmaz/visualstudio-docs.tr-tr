---
title: Görselleştirici güvenlik konuları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, security
- security [Visual Studio], visualizers
ms.assetid: cdd86bd5-b729-409b-a7c6-374efa091eb1
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 51c79c34520c36e51599d4d6135784f493673b62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146462"
---
# <a name="visualizer-security-considerations"></a>Görselleştirici Güvenlik Konuları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Görselleştiricisi yazmak olası güvenlik tehditlerini içerir. Bu olası tehditler için şu anda bilinen bir Exploit yok, ancak geliştiriciler bunların farkında olmalıdır ve gelecekte aşağıda açıklandığı gibi uygun güvenlik önlemleri almalıdır.  
  
 Hata ayıklayıcı Görselleştiriciler kısmi güven uygulaması tarafından izin verilenden daha fazla ayrıcalık gerektiriyor. Kısmi güvenle kodda durdurulduğunda, Görselleştiriciler yüklenmez. Görselleştirici kullanarak hata ayıklamak için, kodu tam güvenle çalıştırmanız gerekir.  
  
## <a name="possible-malicious-debuggee-component"></a>Olası kötü amaçlı hata ayıklanan bileşen  
 Görselleştiriciler en az iki sınıftan oluşur: biri hata ayıklayıcı tarafında ve hata ayıklanan tarafta bir tane. Görselleştiriciler, genellikle özel dizinlere yerleştirilen ayrı derlemelerde dağıtılır, ancak hata ayıklanan içinden de yüklenebilir. Bu durum oluştuğunda, hata ayıklayıcı kodu hata ayıklanan dışına alır ve tam güvenle hata ayıklayıcı içinde çalıştırır.  
  
 Hata ayıklanan yan yana kodu tam güvenle çalıştırmak, hata ayıklama tam güvenilir olmadığında sorunlu hale gelir. Bir Görselleştirici hata ayıklayıcıya ayıklanan bir kısmi güven derlemesini yüklemeye çalışırsa, Visual Studio Görselleştiriciyi sonlandırır.  
  
 Ancak, ikincil bir güvenlik açığı hala mevcuttur. Hata ayıklanan tarafı, başka bir kaynaktan yüklenmiş (hata ayıklanan) bir hata ayıklayıcı tarafı ile ilişkilendirilebilmesi. Hata ayıklanan kenar daha sonra bu güvenilir hata ayıklayıcı tarafında, onun adına eylem gerçekleştirmesini söyleyebilir. Güvenilir hata ayıklayıcı tarafı sınıfı "bu dosyayı sil" mekanizmasını kullanıma sunarsa, örneğin kısmi güven hata ayıklanan Kullanıcı Görselleştirici çağırdığında bu mekanizmayı çağırabilir.  
  
 Bu güvenlik açığını azaltmak için Görselleştiricinizi açığa çıkarması gereken arabirimlerin en az olması gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görselleştiricisi mimarisi](../debugger/visualizer-architecture.md)   
 [Nasıl yapılır: Görselleştirici Yazma](../debugger/how-to-write-a-visualizer.md)   
 [Özel Görselleştiriciler oluşturma](../debugger/create-custom-visualizers-of-data.md)   
 [Hata Ayıklayıcıda Verileri Görüntüleme](../debugger/viewing-data-in-the-debugger.md)
