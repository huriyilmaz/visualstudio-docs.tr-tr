---
title: Etkin betik profil oluşturmaya genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Active Script Profiling
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ce6f7fe29fca2cd17c3dfcce76dac40e422aba4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572725"
---
# <a name="active-script-profiling-overview"></a>Etkin Komut Dosyası Profil Oluşturmaya Genel Bakış
[Etkin komut dosyası profil oluşturucu arabirimleri](../winscript/reference/active-script-profiler-interfaces.md) , bir betik altyapısının profilini oluşturmayı etkinleştirir. Etkin komut dosyası profil oluşturma aşağıdaki bölümlerden oluşur:  
  
- Dil altyapısı  
  
- Ana bilgisayar  
  
- Profil Oluşturucu  
  
## <a name="language-engine"></a>Dil altyapısı  
 Dil altyapısı betiği yürütür. Yürütüldüğü için betik kodunun profilini oluşturmayı etkinleştiren yöntemler sağlar. Profil oluşturma etkinken, dil altyapısı profil oluşturucu COM nesnesinin sınıf tanımlayıcısını (CLSID) bağımsız değişken olarak alır. Profil Oluşturucu COM nesnesinin bir örneğini oluşturur ve çeşitli olaylar gerçekleştiğinde profil oluşturucuya çağırır.  
  
 Dil altyapısı [ıactivescriptprofilercontrol arabirimini](../winscript/reference/iactivescriptprofilercontrol-interface.md)uygular.  
  
> [!NOTE]
> @No__t_0 dil çalışma zamanı, profil oluşturmanın etkinleştirilip etkinleştirilmeyeceğini belirlemede, oluşturma sırasında JS_PROFILER ortam değişkenini denetler. Bu değişken, profil oluşturucunun CLSID 'sine ayarlandıysa, dil çalışma zamanı, oluşturulacak profil oluşturucuyu belirleyen değişkenin değerini kullanarak profil oluşturucu COM nesnesinin bir örneğini oluşturur.  
  
## <a name="host"></a>Ana bilgisayar  
 Konak, dil altyapısını oluşturur ve dil altyapısını yürütülecek betiklerle sağlar. Akıllı ana bilgisayar, hata ayıklama veya profil oluşturma sırasında daha iyi bilgi sağlamak için bir hata ayıklayıcı veya profil oluşturucu tarafından kullanılabilen belge bağlamını de sağlar.  
  
## <a name="profiler"></a>Profil Oluşturucu  
 Profil Oluşturucu, çeşitli olaylar gerçekleştiğinde dil altyapısından gelen çağrıları alır. Profil Oluşturucu bir COM nesnesi olarak kaydettirilmeli ve [ıactivescriptprofilercallback Interface](../winscript/reference/iactivescriptprofilercallback-interface.md) arabirimini gerçekleştirmelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Profil Oluşturucu Arabirimleri](../winscript/reference/active-script-profiler-interfaces.md)