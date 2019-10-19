---
title: Windows komut dosyası Konakları | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Script Host, implementing hosts
ms.assetid: 9d5f6471-b318-40f3-be01-d9cd0b1cdd47
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8468f578ee44487acd2575e81e01d65969110437
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72568817"
---
# <a name="windows-script-hosts"></a>Windows Komut Dosyası Konakları
Microsoft Windows komut dosyası ana bilgisayarı uygularken, ana bilgisayar aşağıdakileri yaptığı sürece bir betik altyapısının yalnızca temel iş parçacığı bağlamında [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) arabirimini çağırdığını varsayabilirsiniz:  
  
- Temel bir iş parçacığı seçer (genellikle ileti döngüsünü içeren iş parçacığı).  
  
- Temel iş parçacığında komut dosyası altyapısını başlatır.  
  
- [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) ve [IActiveScript:: Clone](../winscript/reference/iactivescript-clone.md)durumlarında olduğu gibi, yalnızca temel iş parçacığından gelen betik motoru yöntemlerini çağırır.  
  
- Betik altyapısının Dispatch nesnesini yalnızca temel iş parçacığından çağırır.  
  
- Bir pencere tutamacı sağlanmışsa ileti döngüsünün temel iş parçacığında çalışmasını sağlar.  
  
- Ana bilgisayarın nesne modelindeki nesnelerinin yalnızca temel iş parçacığında kaynak olaylarını sağlar.  
  
  Bu kurallar, tüm tek iş parçacıklı konaklar tarafından otomatik olarak izlenir. Yukarıda açıklanan kısıtlı model, bir ana bilgisayarın, başka bir iş parçacığından (CTRL + BREAK işleyicisi veya benzeri) [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) çağırarak veya bir betiği bir [IActiveScript:: Clone](../winscript/reference/iactivescript-clone.md)kullanarak yeni iş parçacığı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu kısıtlamaların hiçbiri, ücretsiz iş parçacıklı [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) arabirimi ve serbest iş parçacıklı bir nesne modeli uygulamayı seçen bir konak için geçerlidir. Böyle bir ana bilgisayar, kısıtlama olmadan [IActiveScript](../winscript/reference/iactivescript.md) arabirimini herhangi bir iş parçacığından kullanabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Windows Komut Dosyası Arabirimleri](../winscript/windows-script-interfaces.md)