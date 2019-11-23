---
title: Idebugbelgethelper::D efineScriptBlock | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.DefineScriptBlock
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a2418b18e80ac86b672b3847f24ef9084ed1252
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576976"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Belirli bir karakter aralığının, belirtilen betik altyapısı tarafından işlenen bir betik bloğu olduğunu yardımcıya bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ulCharOffset`  
 'ndaki Betik bloğunun başlangıç konumu.  
  
 `cChars`  
 'ndaki Betik bloğundaki karakter sayısı.  
  
 `pas`  
 'ndaki Bu betik bloğunun betik altyapısı.  
  
 `fScriptlet`  
 'ndaki Betik bloğunun bir kod oluşturma yöntemi olup olmadığını gösteren bayrak.  
  
 `pdwSourceContext`  
 dışı Betik bloğunun kaynak bağlamı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Akıllı ana bilgisayar, belgeleri katıştırılmış betik blokları içerdiğinde bu yöntemi kullanabilir. Bir dil motoru, kodu diğer diller için katıştırılmış betikler içerdiğinde bu yöntemi kullanabilir.  
  
 Betik altyapısı, betik bloğundaki tüm sözdizimi renklendirmesinin ve kod bağlamı aramalarının sorumluluğundadır.  
  
 `DefineScriptBlock` yöntemi, metin eklendikten sonra (örneğin, `IDebugDocumentHelper::AddDBCSText` yöntemi kullanılarak), ancak betik bloğu ayrıştırıldıktan önce (örneğin, `IActiveScriptParse ::ParseScriptText` yöntemi kullanılarak) çağrılmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugbelgethelper arabirimini](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Idebugbelgethelper:: AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)