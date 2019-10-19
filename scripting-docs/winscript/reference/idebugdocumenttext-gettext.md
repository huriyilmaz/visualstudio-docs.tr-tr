---
title: 'Idebugdocumenttext:: GetText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetText
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6472c40802fff4dad6e5ecc8f2729c95459e09f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572074"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Karakteri ve/veya karakter konumu aralığı ile ilişkili karakter özniteliklerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cCharacterPosition`  
 'ndaki Karakter konumu aralığının başlangıç konumu.  
  
 `pcharText`  
 [in, out] Bir karakter metin arabelleği. Arabellek `cMaxChars` karakterleri tutabilecek kadar büyük olmalıdır. Bu parametre NULL ise, yöntem karakter döndürmez.  
  
 `pstaTextAttr`  
 [in, out] Bir karakter özniteliği arabelleği. Arabellek `cMaxChars` karakterleri tutabilecek kadar büyük olmalıdır. Bu parametre NULL ise, yöntem öznitelik döndürmez.  
  
 `pcNumChars`  
 [in, out] Döndürülen karakterlerin/özniteliklerin sayısı. Bu metot çağrılmadan önce bu parametrenin sıfır olarak ayarlanması gerekir.  
  
 `cMaxChars`  
 'ndaki Karakter konum aralığındaki karakter sayısı. Döndürülecek en fazla karakter sayısını da belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, karakterleri ve/veya karakter konumu aralığı ile ilişkili karakter özniteliklerini alır. Karakter konumu aralığı, bir karakter konumu ve karakter sayısı ile belirtilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugdocumenttext arabirimi](../../winscript/reference/idebugdocumenttext-interface.md)    
 [SOURCE_TEXT_ATTR Sabit Listesi](../../winscript/reference/source-text-attr-enumeration.md)