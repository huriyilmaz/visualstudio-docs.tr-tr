---
title: 'Ienumdebugapplicationnodes:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugApplicationNodes.Next
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumDebugApplicationNodes::Next
ms.assetid: 925511c8-4f11-423d-ba2d-01589457050c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4ad47c0119eb46c05368fa40ba3a5965fecce0b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573056"
---
# <a name="ienumdebugapplicationnodesnext"></a>IEnumDebugApplicationNodes::Next
Sabit Listesi dizisinde belirtilen sayıda segment alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Next(  
   ULONG                    celt,  
   IDebugApplicationNode**  pprddp,  
   ULONG*                   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `celt`  
 'ndaki Alınacak segment sayısı.  
  
 `pprddp`  
 dışı Alınmakta olan kesimleri temsil eden `IDebugApplicationNode` arabirimlerinden oluşan bir dizi döndürür.  
  
 `pceltFetched`  
 dışı Numaralandırıcı tarafından getirilen parçaların gerçek sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, numaralandırma dizisinde belirtilen sayıda segment alır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IEnumDebugApplicationNodes Arabirimi](../../winscript/reference/ienumdebugapplicationnodes-interface.md)