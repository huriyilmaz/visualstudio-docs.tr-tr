---
title: 'Iactivescriptstats:: GetStat | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStat
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStat
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 096f1cf5b9bf8b5533bd5c36d33f014c747ff9aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574346"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
Standart betik istatistikleriyle birini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `stid`  
 'ndaki Hangi istatistiğin dönebileceği belirtir. Değer olmalıdır:  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|Betiğin başlatılmasından veya istatistiklerin sıfırlanmasından bu yana yürütülen deyimlerin sayısını döndürün.|  
  
 `pluHi`  
 dışı İstatistiği temsil eden 64 bit işaretsiz tamsayının yüksek 32 bitleri.  
  
 `pluLo`  
 dışı İstatistiği temsil eden 64 bit işaretsiz tamsayının düşük 32 biti.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler şunlardır, ancak aşağıdaki tablodaki değerlerle sınırlı değildir.  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, standart betik istatistikleriyle birini döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iactivescriptstats:: GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [IActiveScriptStats Arabirimi](../../winscript/reference/iactivescriptstats-interface.md)