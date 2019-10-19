---
title: 'Itiphandleexception:: CanHandleException | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ICanHandleException.CanHandleException
apilocation:
- scrobj.dll
helpviewer_keywords:
- ICanHandleException::CanHandleException
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c536d35dcb9f0faca8b033ecd39aec520a2e260a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575716"
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
Betik altyapısının çağıranın belirtilen özel durumu işleyemeyeceğini belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pExcepInfo`  
 'ndaki Özel durum işleyici bulunmazsa bildirilecek bilgileri içeren `EXCEPINFO` yapısına yönelik işaretçi.  
  
 `pvar`  
 'ndaki Bir `throw` ifadesiyle oluşturulan değer gibi özel durumla ilişkili bir değer. Bu parametre `NULL` olabilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Çağıran özel durumu işleyebilir|  
|`E_FAIL`|Çağıran özel durumu işleyemez.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0 çağrısı veya benzer bir yöntem, bir özel durumla sonuçlandığında, komut dosyası altyapısı komut dosyasının çağrı zincirinde `ICanHandleException` arabirimini destekleyen ve özel durumu işleyebileceğini belirten bir arayan arar. Hiçbir çağıran özel durumu işleyememesi durumunda, komut dosyası motoru durur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Itiphandleexception arabirimi](../../winscript/reference/icanhandleexception-interface.md)    
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)