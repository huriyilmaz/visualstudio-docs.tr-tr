---
title: 'Idebugbelgethost:: GetDeferredText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetDeferredText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 273b4eb52b7263d34c347dff3a00479945b809df
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569430"
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Özgün ana bilgisayar belgesinde `IDebugDocumentHelper::AddDeferredText` yöntemi kullanılarak eklenen bir karakter aralığı döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwTextStartCookie`  
 'ndaki Metnin başlangıç konumunu temsil eden ana bilgisayar tanımlı tanımlama bilgisi.  
  
 `pcharText`  
 [in, out] Bir karakter metin arabelleği. Bu parametre `NULL`, bu yöntem karakter döndürmez.  
  
 `pstaTextAttr`  
 [in, out] Bir karakter özniteliği arabelleği. Bu parametre `NULL`, bu yöntem öznitelik döndürmez.  
  
 `pcNumChars`  
 [in, out] Döndürülen karakterlerin/özniteliklerin gerçek sayısını gösterir. Bu metot çağrılmadan önce bu parametrenin sıfır olarak ayarlanması gerekir.  
  
 `cMaxChars`  
 'ndaki Döndürülecek en fazla karakter sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_NOTIMPL`|Yöntem uygulanmadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, ana bilgisayar `IDebugDocumentHelper::AddDeferredText`çağırmadığından `E_NOTIMPL`döndürebilir.  
  
> [!NOTE]
> Bu yöntem, özgün belgedeki metni döndürür. Ana bilgisayar, belgedeki düzenlemeleri veya diğer değişiklikleri takip etmez.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugbelgethost arabirimi](../../winscript/reference/idebugdocumenthost-interface.md)   
 [Idebugbelgethelper:: AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE_TEXT_ATTR Sabit Listesi](../../winscript/reference/source-text-attr-enumeration.md)