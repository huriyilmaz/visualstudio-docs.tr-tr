---
title: Windows komut dosyası Konakları | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Windows Script Host, implementing hosts
ms.assetid: 9d5f6471-b318-40f3-be01-d9cd0b1cdd47
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51053dec1f8362aa9eef80e4867d2f92a06454cb
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835335"
---
# <a name="windows-script-hosts"></a>Windows Komut Dosyası Konakları
Microsoft Windows komut dosyası ana bilgisayarı uygularken, ana bilgisayar aşağıdakileri yaptığı sürece bir betik altyapısının yalnızca temel iş parçacığı bağlamında [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) arabirimini çağırdığını varsayabilirsiniz:  
  
- Temel bir iş parçacığı seçer (genellikle ileti döngüsünü içeren iş parçacığı).  
  
- Temel iş parçacığında komut dosyası altyapısını başlatır.  
  
- [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) ve [IActiveScript:: Clone](../winscript/reference/iactivescript-clone.md)durumlarında olduğu gibi, yalnızca temel iş parçacığından gelen betik motoru yöntemlerini çağırır.  
  
- Betik altyapısının Dispatch nesnesini yalnızca temel iş parçacığından çağırır.  
  
- Bir pencere tutamacı sağlanmışsa ileti döngüsünün temel iş parçacığında çalışmasını sağlar.  
  
- Ana bilgisayarın nesne modelindeki nesnelerinin yalnızca temel iş parçacığında kaynak olaylarını sağlar.  
  
  Bu kurallar, tüm tek iş parçacıklı konaklar tarafından otomatik olarak izlenir. Yukarıda açıklanan kısıtlı model, başka bir iş parçacığından [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) çağırarak veya [IActiveScript:: Clone](../winscript/reference/iactivescript-clone.md)kullanarak bir betiği yeni bir iş parçacığında çoğaltmak üzere, bir ana bilgisayarın takılı olmayan bir betiği iptal etmek için yeterince gevşek  
  
## <a name="remarks"></a>Açıklamalar  
 Bu kısıtlamaların hiçbiri, ücretsiz iş parçacıklı [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) arabirimi ve serbest iş parçacıklı bir nesne modeli uygulamayı seçen bir konak için geçerlidir. Böyle bir ana bilgisayar, kısıtlama olmadan [IActiveScript](../winscript/reference/iactivescript.md) arabirimini herhangi bir iş parçacığından kullanabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Windows Komut Dosyası Arabirimleri](../winscript/windows-script-interfaces.md)