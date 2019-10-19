---
title: 'IDebugApplication:: CreateAsyncDebugOperation | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.CreateAsyncDebugOperation
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::CreateAsyncDebugOperation
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1feb8207fb7e7a7faf4427be189c4952139ef32c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575566"
---
# <a name="idebugapplicationcreateasyncdebugoperation"></a>IDebugApplication::CreateAsyncDebugOperation
Belirli bir zaman uyumlu hata ayıklama işlemine zaman uyumsuz erişim sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `psdo`  
 'ndaki Zaman uyumlu hata ayıklama işlemi nesnesi.  
  
 `ppado`  
 dışı Zaman uyumsuz hata ayıklama işlemi nesnesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, dil altyapılarının, hata ayıklayıcı iş parçacığı ile açıkça eşitlemeden ifadeleri zaman uyumsuz olarak değerlendirmesini sağlar. Daha fazla bilgi için bkz. [ıdebugsyncoperation arabirimi](../../winscript/reference/idebugsyncoperation-interface.md) ve [ıdebugger gasyncoperation arabirimi](../../winscript/reference/idebugasyncoperation-interface.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplication arabirimi](../../winscript/reference/idebugapplication-interface.md)    
 [Idebugsyncoperation arabirimi](../../winscript/reference/idebugsyncoperation-interface.md)    
 [IDebugAsyncOperation Arabirimi](../../winscript/reference/idebugasyncoperation-interface.md)