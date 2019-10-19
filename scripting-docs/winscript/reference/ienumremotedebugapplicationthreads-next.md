---
title: 'Ienumremotedebugapplicationthreads:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplicationThreads.Next
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumRemoteDebugApplicationThreads::Next
ms.assetid: d8d10d7e-3468-49be-acf9-d842db9940e7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36d24ffaca05b64c05815124358024d3b88b0d74
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575172"
---
# <a name="ienumremotedebugapplicationthreadsnext"></a>IEnumRemoteDebugApplicationThreads::Next
@No__t_0 yöntemi, numaralandırma dizisinde belirtilen sayıda segment alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Next(  
   ULONG                            celt,  
   IRemoteDebugApplicationThread**  pprdat,  
   ULONG*                           pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `celt`  
 'ndaki Alınacak segment sayısı.  
  
 `pprdat`  
 dışı Alınmakta olan kesimleri temsil eden `IRemoteDebugApplicationThread` arabirimlerinden oluşan bir dizi döndürür.  
  
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
 [IEnumRemoteDebugApplicationThreads Arabirimi](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)