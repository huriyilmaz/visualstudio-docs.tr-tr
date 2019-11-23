---
title: 'Idebugbelgethelper:: AddDeferredText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDeferredText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDeferredText
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1aae73e44059b1f07fa4cb54f40cdcd12e564a8f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577047"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Yardım 'a verilen metnin kullanılabilir olduğunu ancak karakterleri sağlamadığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cChars`  
 'ndaki Eklenecek karakter sayısı (Unicode).  
  
 `dwTextStartCookie`  
 'ndaki Metnin başlangıç konumunu temsil eden ana bilgisayar tanımlı tanımlama bilgisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_FAIL`|Yöntem başarısız oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, ana bilgisayarın, gerek duyuluncaya kadar eklenecek karakterleri sağlamayı erteetmesine izin verir. böylece, yardım 'ın doğru bildirimler ve boyut bilgileri oluşturmasına izin verir. `dwTextStartCookie` parametresi, ana bilgisayar tarafından tanımlanan ve metnin başlangıç konumunu temsil eden bir tanımlama bilgisidir. `IDebugDocumentText::GetText` sonraki çağrıların bu tanımlama bilgisini sağlaması gerekir. Örneğin, DBCS 'deki metni temsil eden bir konakta, tanımlama bilgisi bir bayt kayması olabilir.  
  
 `IDebugDocumentText::GetText` tek bir çağrının, `AddDeferredText`birden çok çağrıdan karakter alabilirim olduğu varsayılır. Yardımcı sınıflar aynı zamanda aynı gecikmeli karakter aralığını birden çok kez sorabilir.  
  
> [!NOTE]
> `AddDeferredText` çağrıları, `AddUnicodeText` veya `AddDBCSText`çağrılarında karışık olmamalıdır. Bu durumda `E_FAIL` döndürülür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugbelgethelper arabirimini](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Idebugbelgethelper:: AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [Idebugbelgethelper:: AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)