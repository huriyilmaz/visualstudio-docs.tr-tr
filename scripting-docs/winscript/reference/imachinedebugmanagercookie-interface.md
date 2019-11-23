---
title: Imachinedebugmanagercookie arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerCookie interface
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b39c286f389c99187b0f3250fc68af92ff5dcc8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573879"
---
# <a name="imachinedebugmanagercookie-interface"></a>IMachineDebugManagerCookie Arabirimi
`IMachineDebugManager` arabirimine benzer şekilde, `IMachineDebugManagerCookie` arabirimi hata ayıklama tanımlama bilgilerini destekler.  
  
 Bu arabirim (`IDebugCookie` arabirimi ile birlikte), komut dosyalarının hata ayıklayıcının Bu betiklerin izlenmesini gerektirmeksizin bir betik hata ayıklayıcısı işleminde çalışmasına izin verir.  
  
 Betik hata ayıklayıcısı Işlem hata ayıklama yöneticisinde `IDebugCookie::SetDebugCookie` yöntemini çağırır (PDM). Daha sonra, PDM bu tanımlama bilgisini, `IMachineDebugManagerCookie` arabiriminin yöntemlerini kullanarak makine hata ayıklama Yöneticisi 'ne (MDM) veya makineye bir betik uygulaması ekleme veya kaldırma isteği ile birlikte gönderir. MDM daha sonra değişikliğin her hata ayıklayıcısını, bu tanımlama bilgisine sahip olanlar hariç bilgilendirir.  
  
 `IUnknown`devralınan yöntemlere ek olarak, `IMachineDebugManagerCookie` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Çalışan uygulama listesine bir uygulama ekler.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Çalışan uygulamaların geçerli listesinin bir Numaralandırıcı döndürür.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Çalışan uygulama listesinden bir uygulamayı kaldırır.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Imachinedebugmanager arabirimi](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IDebugCookie Arabirimi](../../winscript/reference/idebugcookie-interface.md)