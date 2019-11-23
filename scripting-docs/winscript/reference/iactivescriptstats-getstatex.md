---
title: 'Iactivescriptstats:: GetStatEx | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStatEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStatEx
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ca7cdb81fd7e228b26bfaa12d45e81335674a74
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576118"
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
Özel Betik istatistiğini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `guid`  
 'ndaki Hangi istatistiğin dönebileceği belirtir. Belirli bir GUID 'ye karşılık gelen istatistiğin sözdizimi, tamamen tanımlı bir altyapısıdır.  
  
 `pluHi`  
 dışı İstatistiği temsil eden 64 bit işaretsiz tamsayının yüksek 32 bitleri.  
  
 `pluLo`  
 dışı İstatistiği temsil eden 64 bit işaretsiz tamsayının düşük 32 biti.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_NOTIMPL`|Yöntem uygulanmadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, özel bir betik altyapısının özel bir konağa anlamlı istatistikler döndürmesini sağlar.  
  
> [!NOTE]
> Bu yöntem şu anda uygulanmadı.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iactivescriptstats:: GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [IActiveScriptStats Arabirimi](../../winscript/reference/iactivescriptstats-interface.md)