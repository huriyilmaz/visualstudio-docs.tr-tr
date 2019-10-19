---
title: 'Iactivescriptauthor:: GetScriptTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptTextAttributes
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f89c7b654cc2ac7248598ee6498a3a290d17e2ef
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72563141"
---
# <a name="iactivescriptauthorgetscripttextattributes"></a>IActiveScriptAuthor::GetScriptTextAttributes
Bir betik bloğunun metin özniteliklerini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetScriptTextAttributes(  
    LPCOLESTR        pszCode,  
    ULONG            cch,  
    LPCOLESTR        pszDelimiter,  
    DWORD            dwFlags,  
    SOURCE_TEXT_ATTR *pattr);  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszCode`  
 [in, size_is (`cch`)] Betik bloğunun metni. Bu dize, null olarak sonlandırılmış olması gerekmez.  
  
 `cch`  
 'ndaki @No__t_0 ve `pattr` parametreleri için kullanılan boyut.  
  
 `pszDelimiter`  
 'ndaki Komut dosyası sınırlayıcısından oluşan adres. @No__t_0 metin akışından ayrıştırıldığında, ana bilgisayar genellikle bir sınırlayıcı (örneğin, iki tek tırnak işareti) kullanır ve bu kod oluşturma yöntemi sonunu algılar. Betik bloğunun sonunu tanımlamak için sınırlayıcı yoksa bu parametreyi NULL olarak ayarlayın.  
  
 `dwFlags`  
 'ndaki Betik bloğunun metin öznitelikleriyle ilişkili bayraklar. Aşağıdaki değerlerin bir birleşimi olabilir:  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|SOURCETEXT_ATTR_IDENTIFIER özniteliğine sahip tanımlayıcıları ve SOURCETEXT_ATTR_MEMBERLOOKUP özniteliğine sahip nokta işleçlerini belirler.|  
|GETATTRFLAG_THIS|0x0100|SOURCETEXT_ATTR_THIS özniteliğine sahip geçerli nesneyi belirler.|  
|GETATTRFLAG_HUMANTEXT|0x8000|SOURCETEXT_ATTR_HUMANTEXT özniteliğine sahip dize içeriğini ve açıklama metnini belirler.|  
  
 `pattr`  
 [in, Out, size_is (`cch`)] Betik blok kodu için renk bilgileri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iactivescriptauthor arabirimi](../../winscript/reference/iactivescriptauthor-interface.md)    
 [SOURCE_TEXT_ATTR Sabit Listesi](../../winscript/reference/source-text-attr-enumeration.md)