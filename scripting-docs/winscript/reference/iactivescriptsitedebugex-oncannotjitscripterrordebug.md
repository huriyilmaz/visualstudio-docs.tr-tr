---
title: 'Iactivescriptsitedebugex:: Oncannotjscripterrordebug | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7358d2b372f0801b8c45816e1fc36018b37799b2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572188"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Işlem hata ayıklama Yöneticisi bir tam zamanında betik hata ayıklayıcısı bulamazsa ana bilgisayarı bir betik çalışma zamanı hatası hakkında bilgilendirir.  
  
 Ana bilgisayarınızda bir hata ayıklayıcı uygulamak için [ıactivescriptsitedebug:: OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)öğesini işlemeniz gerekir. Ana bilgisayar, bir kullanıcı eylemine bağlı olarak, hata ayıklayıcıyı ekleyebilir ve döndürebilir ya da OnScriptErrorDebug `pfEnterDebugger` parametresinde hata ayıklayıcının başlangıcını döndürebilir. Işlem hata ayıklama Yöneticisi tarafından yorumlanabilecek dış hata ayıklayıcıları olmasa bile, çalışma zamanı hatası hakkında bildirim almak için bu arabirimi de uygulamalısınız.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pErrorDebug`  
 'ndaki Oluşan çalışma zamanı hatası.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 dışı Kullanıcı hata ayıklamadan devam etmeye karar verirse [ıactivescriptsitedebug:: OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) çağrısı yapılıp yapılmayacağını belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir bildirim almak için bu arabirimi de uygulamalısınız.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptSiteDebugEx Arabirimi](../../winscript/reference/iactivescriptsitedebugex-interface.md)