---
title: 'IRemoteDebugApplication:: ResumeFromBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ResumeFromBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ResumeFromBreakPoint
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7fead9c14efbe73bd006a5ff3e1cfb10ad40404b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577454"
---
# <a name="iremotedebugapplicationresumefrombreakpoint"></a>IRemoteDebugApplication::ResumeFromBreakPoint
Şu anda bir kesme noktasında olan bir uygulamaya devam eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `prptFocus`  
 'ndaki Adımlama modlarında, Adımlama modundan etkilenecek iş parçacığı.  
  
 `bra`  
 'ndaki Uygulama sürdürülmeden gerçekleştirilecek eylem.  
  
 `era`  
 'ndaki Bir hata nedeniyle uygulamanın durdurulduğu durumda gerçekleştirilecek eylem.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, şu anda bir kesme noktasında olan bir uygulamayı devam ettirir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IRemoteDebugApplication arabirimi](../../winscript/reference/iremotedebugapplication-interface.md)    
 [Breakresumeaction numaralandırması](../../winscript/reference/breakresumeaction-enumeration.md)    
 [ERRORRESUMEACTION Sabit Listesi](../../winscript/reference/errorresumeaction-enumeration.md)