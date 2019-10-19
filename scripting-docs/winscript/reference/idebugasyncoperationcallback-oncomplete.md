---
title: 'Icodegasyncoperationcallback:: Ontamamlan| Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperationCallBack.onComplete
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugAsyncOperationCallBack::onComplete
ms.assetid: d4023f5a-41f9-4948-b0dc-3317d61bb783
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a15ae57d64d2b1e7be867c20e9683e4aaa415974
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573237"
---
# <a name="idebugasyncoperationcallbackoncomplete"></a>IDebugAsyncOperationCallBack::onComplete
Zaman uyumsuz bir hata ayıklama işleminden elde edilen bir sonuç olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT onComplete();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem hiçbir parametre alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem bir `IDebugAsyncOperation` nesnesinden kullanılabilir bir sonuç olduğunu bildirir. Olay, hata ayıklayıcı iş parçacığında ateşlenir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Ihata ayıklama Gasyncoperationcallback arabirimi](../../winscript/reference/idebugasyncoperationcallback-interface.md)    
 [IDebugAsyncOperation Arabirimi](../../winscript/reference/idebugasyncoperation-interface.md)