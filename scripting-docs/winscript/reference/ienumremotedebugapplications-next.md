---
title: 'Ienumremotedebugapplications:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplications.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumRemoteDebugApplications::Next
ms.assetid: 33f6c620-6dd3-4057-b982-b88a7a1f02b4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a9ebcbbd786ba8545e19b9833d26e5e385738c4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575208"
---
# <a name="ienumremotedebugapplicationsnext"></a>IEnumRemoteDebugApplications::Next
@No__t_0 yöntemi, numaralandırma dizisinde belirtilen sayıda segment alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Next(  
   ULONG                      celt,  
   IRemoteDebugApplication**  ppda,  
   ULONG*                     pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `celt`  
 'ndaki Alınacak segment sayısı.  
  
 `ppda`  
 dışı Alınmakta olan kesimleri temsil eden `IRemoteDebugApplication` arabirimlerinden oluşan bir dizi döndürür.  
  
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
 [IEnumRemoteDebugApplications Arabirimi](../../winscript/reference/ienumremotedebugapplications-interface.md)