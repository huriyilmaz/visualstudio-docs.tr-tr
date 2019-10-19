---
title: Idebugexpressioncontext::P arseLanguageText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext.ParseLanguageText
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::ParseLanguageText
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0493adde76e029088b637be3c6aaf02c55caaace
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573160"
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
Belirtilen metin için bir hata ayıklama ifadesi oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstrCode`  
 'ndaki İfade veya deyimler için metin sağlar.  
  
 `nRadix`  
 'ndaki Kullanılacak Radix.  
  
 `pstrDelimiter`  
 'ndaki Komut dosyası blok sınırlayıcısı. @No__t_0 metin akışından ayrıştırıldığında, ana bilgisayar genellikle iki tek tırnak işareti (' ') gibi bir sınırlayıcı kullanır ve komut dosyası bloğunun sonunu algılar. Bu parametre, ana bilgisayarın kullandığı sınırlayıcıyı belirtir ve betik altyapısının bazı koşullu temel bir ön işleme sağlamasına izin verir (örneğin, tek tırnak işaretini ['] sınırlayıcı olarak kullanılmak üzere iki tek tırnak işaretiyle değiştirme). Betik altyapısının bu bilgileri kullanması tam olarak nasıl (ve ne olursa) komut dosyası altyapısına bağlıdır. Ana bilgisayar betik bloğunun sonunu işaretlemek için bir sınırlayıcı kullanmadığından bu parametreyi `NULL` olarak ayarlayın.  
  
 `dwFlags`  
 'ndaki Aşağıdaki hata ayıklama metin bayraklarının birleşimi:  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Metnin bir deyimin aksine bir ifade olduğunu gösterir. Bu bayrak, metnin bazı diller tarafından ayrıştırılma şeklini etkileyebilir.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Bir dönüş değeri varsa, bu, çağıran tarafından kullanılır.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Yan etkilere izin vermeyin. Bu bayrak ayarlandıysa, ifadenin değerlendirmesi çalışma zamanı durumunu değiştirmez.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Metnin değerlendirmesi sırasında kesme noktalarına izin verir. Bu bayrak ayarlanmamışsa, metnin değerlendirmesi sırasında kesme noktaları yok sayılır.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Metnin değerlendirmesi sırasında hata raporlarına izin verir. Bu bayrak ayarlanmamışsa, değerlendirme sırasında hatalar konağa bildirilmez.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|İfadenin kendisini çalıştırmak yerine bir kod bağlamı olarak değerlendirilip değerlendirilmeyeceğini belirtir|  
  
 `ppe`  
 dışı Belirtilen metin için hata ayıklama ifadesini döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, belirtilen metin için bir hata ayıklama ifadesi oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugExpressionContext Arabirimi](../../winscript/reference/idebugexpressioncontext-interface.md)