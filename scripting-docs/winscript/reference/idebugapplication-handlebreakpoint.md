---
title: 'IDebugApplication:: HandleBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleBreakPoint
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30937817424e88f80cfa6afa8c874adfd2b2687b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574969"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Geçerli iş parçacığının, hata ayıklayıcı IDE 'sine kesme noktasına yönelik bir bildirim almasına ve bildirimine neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `br`  
 'ndaki Kesmenin nedeni.  
  
 `pbra`  
 dışı Hata ayıklayıcı uygulamayı sürdürür gerçekleştirilecek eylem.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir dil altyapısı, bu yöntemi bir kesme noktasına rastbir iş parçacığı bağlamında çağırır. Bu yöntem, geçerli iş parçacığını engeller ve hata ayıklayıcı IDE 'sine bir kesme noktası bildirimi gönderir. Hata ayıklayıcı uygulamayı sürdürürse, `pbra` parametresi gerçekleştirilecek eylemi belirtir.  
  
> [!NOTE]
> Dil altyapısı, yığın çerçevelerini numaralandırma veya kesme noktası sırasında ifadeleri değerlendirme gibi görevleri yapmak için iş parçacığı tarafından çağrılabilir.  
  
 Bu yöntem `IApplicationDebugger::onHandleBreakPoint` çağırmasına neden olur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplication arabirimi](../../winscript/reference/idebugapplication-interface.md)   
 [Iapplicationdebugger:: onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [Breakreason numaralandırması](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION Sabit Listesi](../../winscript/reference/breakresumeaction-enumeration.md)