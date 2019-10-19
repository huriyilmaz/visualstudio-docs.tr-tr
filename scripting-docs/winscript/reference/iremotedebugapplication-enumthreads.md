---
title: 'IRemoteDebugApplication:: EnumThreads | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.EnumThreads
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::EnumThreads
ms.assetid: b4d7294c-1f15-4f7e-bdfd-700e3bf98cea
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 759ecc2da982e840e059e0d96d2b630190527d43
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573845"
---
# <a name="iremotedebugapplicationenumthreads"></a>IRemoteDebugApplication::EnumThreads
Uygulamayla ilişkilendirilmesi bilinen tüm iş parçacıklarını numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT EnumThreads(  
   IEnumRemoteDebugApplicationThreads**  pperdat  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pperdat`  
 dışı Uygulamayla ilişkilendirilmesi bilinen tüm iş parçacıklarını listeleyen Numaralandırıcı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, uygulamayla ilişkilendirilmesi bilinen tüm iş parçacıklarını numaralandırır. Yeni iş parçacıkları dilediğiniz zaman eklenebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IRemoteDebugApplication Arabirimi](../../winscript/reference/iremotedebugapplication-interface.md)