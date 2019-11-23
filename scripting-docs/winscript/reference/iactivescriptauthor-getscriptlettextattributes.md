---
title: 'Iactivescriptauthor:: GetScriptletTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptletTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptletTextAttributes
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4cd0090b9ade47ad37acf6d285ec7f072f1ea5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576176"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
Bir kod oluşturma yöntemi öğesinin metin özniteliklerini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszCode`  
 [in, size_is (`cch`)] Kod oluşturma yöntemi metni. Bu dize, null olarak sonlandırılmış olması gerekmez.  
  
 `cch`  
 'ndaki `pszCode` ve `pattr` parametreleri için kullanılan boyut.  
  
 `pszDelimiter`  
 'ndaki Son kod oluşturma yöntemi sınırlayıcısı adresi. `pszCode` metin akışından ayrıştırıldığında, ana bilgisayar genellikle bir sınırlayıcı (örneğin, iki tek tırnak işareti) kullanır ve bu kod oluşturma yöntemi sonunu algılar. Kod oluşturma yöntemi sonunu tanımlamak için hiçbir sınırlayıcı kullanılmazsa bu parametreyi NULL olarak ayarlayın.  
  
 `dwFlags`  
 'ndaki Kod oluşturma yöntemi 'ın metin öznitelikleriyle ilişkili bayraklar. Aşağıdaki değerlerin bir birleşimi olabilir.  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|SOURCETEXT_ATTR_IDENTIFIER özniteliğine sahip tanımlayıcıları ve SOURCETEXT_ATTR_MEMBERLOOKUP özniteliğine sahip nokta işleçlerini tanımla.|  
|GETATTRFLAG_THIS|0x0100|SOURCETEXT_ATTR_THIS özniteliğine sahip geçerli nesneyi belirler.|  
|GETATTRFLAG_HUMANTEXT|0x8000|SOURCETEXT_ATTR_HUMANTEXT özniteliğine sahip dize içeriğini ve açıklama metnini belirler.|  
  
 `pattr`  
 [in, Out, size_is (`cch`)] Kod oluşturma yöntemi kodu için renk bilgileri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iactivescriptauthor arabirimi](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Iactivescriptauthor:: GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [SOURCE_TEXT_ATTR Sabit Listesi](../../winscript/reference/source-text-attr-enumeration.md)