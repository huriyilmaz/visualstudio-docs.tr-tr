---
title: 'Icriptentry:: GetRange | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetRange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a6e1b1600c93aa05bbe9669fb57a23a8c9344a1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575429"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Bir girdinin başlangıç konumunu ve uzunluğunu döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pichMin`  
 dışı Bir betik bloğunu belirten `IScriptEntry` nesneler için 0 döndürür.  
  
 Bir işlev nesnesi belirten `IScriptEntry` nesneler için, geçerli betik bloğundaki işlevin başlangıç konumunu döndürür.  
  
 @No__t_0 nesneler için 0 döndürür.  
  
 `pcch`  
 dışı Bir betik bloğunu belirten `IScriptEntry` nesneler için, metnin uzunluğunu döndürür.  
  
 Bir işlev nesnesi belirten `IScriptEntry` nesneler için, işlev tanımının uzunluğunu döndürür.  
  
 @No__t_0 nesneler için girdinin uzunluğunu döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IScriptEntry Arabirimi](../../winscript/reference/iscriptentry-interface.md)