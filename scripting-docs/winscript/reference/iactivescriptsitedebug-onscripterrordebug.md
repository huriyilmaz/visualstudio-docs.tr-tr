---
title: 'Iactivescriptsitedebug:: OnScriptErrorDebug | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::OnScriptErrorDebug
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 894767b3dae9db54e8bc438a82b27195308a4342
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572212"
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
Akıllı ana bilgisayarın çalışma zamanı hatalarının nasıl işleneceğini belirlemesine izin verir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pErrorDebug`  
 'ndaki Oluşan çalışma zamanı hatası  
  
 `pfEnterDebugger`  
 dışı JıT hata ayıklaması yapmak için hatanın hata ayıklayıcıya geçirilip geçirilmeyeceğini belirten bayrak.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 dışı Kullanıcı hata ayıklamadan devam etmeye karar verdiğinde `IActiveScriptSite::OnScriptError` çağırılacağını belirten bayrak.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler şunlardır, ancak aşağıdaki tablodaki değerle sınırlı değildir.  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir akıllı ana bilgisayar, çalışma zamanı hatalarının nasıl işleneceğini öğrenmek için bu yöntemi kullanabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptSiteDebug Arabirimi](../../winscript/reference/iactivescriptsitedebug-interface.md)