---
title: 'Idebugbelgethelper:: Init | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Init
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Init
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13e6379052707aa44c0fa52f4cb30db2c4c4fa99
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576859"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
`Init` yöntemi bir hata ayıklama belgesi yardımcısını bir ad ve başlangıç öznitelikleri ile başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pda`  
 'ndaki Bu belgeyle ilişkili hata ayıklama uygulaması.  
  
 `pszShortName`  
 'ndaki Belgenin kısa adını içeren null ile sonlandırılmış bir dize.  
  
 `pszLongName`  
 'ndaki Belgenin uzun adını içeren null ile sonlandırılmış bir dize.  
  
 `docAttr`  
 'ndaki Metin belgesi özniteliklerini belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem bir hata ayıklama belgesi yardımcısını bir ad ve başlangıç öznitelikleri ile başlatır.  
  
 `IDebugDocumentHelper::Attach` çağrılana kadar bu belge ağaçta görünmez.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugbelgethelper:: Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [Idebugbelgethelper arabirimini](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT_DOC_ATTR Sabitleri](../../winscript/reference/text-doc-attr-constants.md)