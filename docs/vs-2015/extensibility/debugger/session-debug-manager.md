---
title: Oturum hata ayıklama Yöneticisi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fd7c7555c19f850a15161f6fba00b1184621a9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157831"
---
# <a name="session-debug-manager"></a>Oturum Hata Ayıklama Yöneticisi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Oturum hata ayıklama Yöneticisi (SDM), herhangi bir sayıda makinede birden çok işlemde bulunan her türlü programda hata ayıklama altyapısını (DE) yönetir. Bir hata ayıklama altyapısı Çoğullayıcı olmanın yanı sıra, SDM, IDE 'ye hata ayıklama oturumunun Birleşik bir görünümünü sağlar.  
  
## <a name="session-debug-manager-operation"></a>Oturum hata ayıklama Yöneticisi Işlemi  
 Oturum hata ayıklama Yöneticisi (SDM), DE yönetir. Aynı anda bir makinede çalışan birden fazla hata ayıklama altyapısı olabilir. DEs çoğullanır olması için, SDM DEs 'ten bir dizi arabirimi sarmalamalı ve bunları tek bir arabirim olarak IDE 'ye gösterir.  
  
 Performansı artırmak için bazı arabirimler çoğullanmış değildir. Bunun yerine, doğrudan DE ile kullanılır ve bu arayüzlere yapılan çağrılar SDM 'ye gitmez. Örneğin, bellek, kod ve belge bağlamlarına göre kullanılan arabirimler, belirli bir şekilde hata ayıkladığı belirli bir programdaki belirli bir yönerge, bellek veya belgeye başvurduğundan çoğullanabilir değildir. Bu iletişim düzeyine dahil olması gereken başka bir DE yok.  
  
 Bu, tüm bağlamlarda doğru değildir. İfade değerlendirme bağlamı arabirimine yapılan çağrılar SDM aracılığıyla gider. İfade değerlendirmesi sırasında, SDM, bu ifade değerlendirildiği zaman, aynı iş parçacığında çalışmakta olabilecek programlarda hata ayıklama [yapan, aynı](../../extensibility/debugger/reference/idebugexpression2.md) işlemde çalışan birden fazla des içerebilir.  
  
 SDM genellikle bir yetkilendirme mekanizması işlevi görür, ancak bir yayın mekanizması işlevi görebilir. Örneğin, ifade değerlendirmesi sırasında, SDM, belirli bir iş parçacığında kod çalıştırabilecekleri tüm DEs 'e bildirimde bulunan bir yayın mekanizması olarak görev yapar. Benzer şekilde, SDM bir durdurma olayı aldığında, çalışmayı durdurması gereken tüm programları yayınlar. Bir adım çağrıldığında, SDM çalışmaya devam edebilecekleri tüm programlara yayınlar. Kesme noktaları aynı zamanda her da ' a yayınlanır.  
  
 SDM geçerli program, iş parçacığı veya yığın çerçevesini izlemez. İşlem, program ve iş parçacığı bilgileri, belirli hata ayıklama olaylarıyla birlikte SDM 'ye gönderilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)   
 [Hata ayıklayıcı bileşenleri](../../extensibility/debugger/debugger-components.md)   
 [Hata Ayıklayıcı Bağlamları](../../extensibility/debugger/debugger-contexts.md)
