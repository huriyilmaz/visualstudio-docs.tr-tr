---
title: 'Iactivescriptauthor:: GetEventHandler | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetEventHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetEventHandler
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c69b32f0040ea6d52e0712b8e1813cc5a0b40c58
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576225"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Belirtilen özniteliklere sahip olan kod oluşturma yöntemi döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdisp`  
 'ndaki Kod oluşturma yöntemi eklendiği `NamedItem` karşılık gelen `IDispatch` nesnesi.  
  
 `pszItem`  
 'ndaki Konaktaki tam kod oluşturma yöntemi adının üst düzey tanımlayıcısının arabellek adresi.  
  
 `pszSubItem`  
 'ndaki Konaktaki tam kod oluşturma yöntemi adının ikinci düzey tanımlayıcısının arabellek adresi. Ad yalnızca bir düzey içeriyorsa NULL olarak ayarlanır.  
  
 `pszEvent`  
 'ndaki Olay adını içeren bir arabelleğin adresi. Kod oluşturma yöntemi bu olay için bir olay işleyicisidir.  
  
 `ppse`  
 dışı Belirtilen özniteliklere sahip olan kod oluşturma yöntemi `IScriptEntry` arabirimine bir işaretçi alan bir değişkenin adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iactivescriptauthor arabirimi](../../winscript/reference/iactivescriptauthor-interface.md)    
 [IScriptEntry Arabirimi](../../winscript/reference/iscriptentry-interface.md)