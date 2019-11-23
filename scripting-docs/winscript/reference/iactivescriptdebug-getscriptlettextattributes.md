---
title: 'Iactivescriptdebug:: GetScriptletTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptletTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptletTextAttributes
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a5dd9e219e51b001659225636396fe45ac815b9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572800"
---
# <a name="iactivescriptdebuggetscriptlettextattributes"></a>IActiveScriptDebug::GetScriptletTextAttributes
Rastgele bir kod oluşturma yöntemi için metin özniteliklerini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstrCode`  
 'ndaki Kod oluşturma yöntemi metni. Bu dize null olarak sonlandırılmamalıdır.  
  
 `uNumCodeChars`  
 'ndaki Kod oluşturma yöntemi metnindeki karakterlerin sayısı.  
  
 `pstrDelimiter`  
 'ndaki Son kod oluşturma yöntemi sınırlayıcısı adresi. `pstrCode` metin akışından ayrıştırıldığında, ana bilgisayar genellikle iki tek tırnak işareti (' ') gibi bir sınırlayıcı kullanır, bu da kod oluşturma yöntemi sonunu algılar. Bu parametre, ana bilgisayarın kullandığı sınırlayıcıyı belirtir ve betik altyapısının bazı koşullu temel bir ön işleme sağlamasına izin verir (örneğin, tek tırnak işaretini ['] sınırlayıcı olarak kullanılmak üzere iki tek tırnak işaretiyle değiştirme). Betik altyapısının bu bilgileri kullanması tam olarak nasıl (ve ne olursa) komut dosyası altyapısına bağlıdır. Konak, kod oluşturma yöntemi sonunu işaretlemek için bir sınırlayıcı kullanmadığından bu parametreyi NULL olarak ayarlayın.  
  
 `dwFlags`  
 'ndaki Kod oluşturma yöntemi ile ilişkili bayraklar. Şu değerlerin bir birleşimi olabilir:  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Tanımlayıcıların ve nokta işleçlerinin sırasıyla SOURCETEXT_ATTR_IDENTIFIER ve SOURCETEXT_ATTR_MEMBERLOOKUP bayraklarıyla tanımlanması gerektiğini gösterir.|  
|GETATTRFLAG_THIS|0x0100|Geçerli nesne için tanımlayıcının SOURCETEXT_ATTR_THIS bayrağıyla tanımlanması gerektiğini gösterir.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Dize içeriği ve Açıklama metninin SOURCETEXT_ATTR_HUMANTEXT bayrağıyla tanımlanması gerektiğini gösterir.|  
  
 `pattr`  
 [in, out] Döndürülen öznitelikleri içeren arabellek.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IDebugDocumentText` arabirimini uygulayan bir akıllı ana bilgisayar, `IDebugDocumentText::GetText` yöntemine yapılan çağrıları devretmek için bu yöntemi kullanabilir.  
  
 Bu çağrı, scriptto ifadesi olması ve bir komut dosyası bloğundan farklı bir sözdizimine sahip olabileceği için sağlanır. Aynı söz dizimine sahip olmaları durumunda, bu yöntemin uygulanması `GetScriptTextAttributes` yönteminin uygulanmasıyla aynı olacaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iactivescriptdebug arabirimi](../../winscript/reference/iactivescriptdebug-interface.md)   
 [Iactivescriptdebug:: GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [Idebugdocumenttext arabirimi](../../winscript/reference/idebugdocumenttext-interface.md)   
 [Idebugdocumenttext:: GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE_TEXT_ATTR Sabit Listesi](../../winscript/reference/source-text-attr-enumeration.md)