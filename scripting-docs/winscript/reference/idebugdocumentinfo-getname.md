---
title: 'Idebugdocumentınfo:: GetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetName
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc098da29367a322bd93b4f60ba0e090aee9ee91
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570962"
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
Belirtilen belge adını döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dnt`  
 'ndaki Döndürülecek belge adının türü.  
  
 `pbstrName`  
 dışı Adı içeren dize.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_FAIL`|Belirtilen belge adı bilinmiyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, belirtilen belge adını döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugdocumentınfo arabirimi](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [DOCUMENTNAMETYPE Sabit Listesi](../../winscript/reference/documentnametype-enumeration.md)