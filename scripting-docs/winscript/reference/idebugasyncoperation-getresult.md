---
title: 'Ihata ayıklama Gasyncoperation:: GetResult | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.GetResult
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::GetResult
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55c51649a5bc3094dd306166e013a892ce67e236
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573289"
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
Zaman uyumlu hata ayıklama işleminden dönüş değeri ve dönüş nesnesi parametresi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `phrResult`  
 dışı İşlem tamamlandıysanız, `phrResult` `IDebugSyncOperation::Execute`dönüş değeridir.  
  
 `ppunkResult`  
 dışı İşlem tamamlandıysanız, `ppunkResult` işlem tarafından döndürülen nesne parametresidir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_PENDING`|İşlem tamamlanmadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 İşlem tamamlanırsa, bu yöntem `IDebugSyncOperation::Execute``HRESULT` ve nesne parametresini döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Ihata ayıklama Gasyncoperation arabirimi](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)