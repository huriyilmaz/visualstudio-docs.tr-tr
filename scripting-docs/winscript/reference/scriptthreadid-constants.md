---
title: SCRIPTTHREADıD sabitleri | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADID
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADID
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf1b23b191bda29b00bf29f482332301897f9f37
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575661"
---
# <a name="scriptthreadid-constants"></a>SCRIPTTHREADID Sabitleri
İş parçacığı türünü belirtmek için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Sabitler  
  
|Sabit|Değer|Anlamı|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|Yürütülmekte olan iş parçacığı.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|Temel iş parçacığı; diğer bir deyişle, komut dosyası altyapısının örneklendiği iş parçacığı.|  
|SCRIPTTHREADID_ALL|Ffffffff|Tüm iş parçacıkları.|  
  
## <a name="remarks"></a>Açıklamalar  
 `SCRIPTTHREADID` türü `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState`ve `IActiveScript::InterruptScriptThread`tarafından kullanılır, ancak sabitler yalnızca `IActiveScript::GetScriptThreadState` ve `IActiveScript::InterruptScriptThread`tarafından kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScript:: GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript:: Getscriptthreadıd](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript:: GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)