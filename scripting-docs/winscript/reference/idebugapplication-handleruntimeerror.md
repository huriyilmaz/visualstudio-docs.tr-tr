---
title: 'IDebugApplication:: HandleRuntimeError | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleRuntimeError
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleRuntimeError
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fd4ba2b811cd6c4e38c10a0c68c5808f2c0870a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574327"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Geçerli iş parçacığının, hata ayıklayıcı IDE 'sine hata bildirimini ve hata bildirimini göndereceğini sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pErrorDebug`  
 'ndaki Oluşan hata.  
  
 `pScriptSite`  
 'ndaki İş parçacığının betik sitesi.  
  
 `pbra`  
 dışı Hata ayıklayıcı uygulamayı sürdürür gerçekleştirilecek eylem.  
  
 `perra`  
 dışı Hata ayıklayıcı hata oluşursa uygulamayı sürdürür gerçekleştirilecek eylem.  
  
 `pfCallOnScriptError`  
 dışı Altyapının `IActiveScriptSite::OnScriptError` yöntemini çağırması gerekiyorsa `TRUE` bayrak.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir dil altyapısı, çalışma zamanı hatasına neden olan bir iş parçacığının bağlamında bu yöntemi çağırır. Bu yöntem, geçerli iş parçacığının, hata ayıklayıcı IDE 'sine gönderilmek üzere bir hata bildirimi engellemesini ve göndereceğini sağlar. Hata ayıklayıcı IDE uygulamayı devam ettirir, bu yöntem gerçekleştirilecek eylem ile birlikte döndürür.  
  
> [!NOTE]
> Çalışma zamanı hatasında, dil motoru, yığın çerçevelerini numaralandırma veya ifadeleri değerlendirme gibi görevleri yapmak için iş parçacığı tarafından çağrılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplication arabirimi](../../winscript/reference/idebugapplication-interface.md)   
 [Iactivescripterrordebug arabirimi](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [Iactivescriptsite](../../winscript/reference/iactivescriptsite.md)   
 [Breakresumeaction numaralandırması](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION Sabit Listesi](../../winscript/reference/errorresumeaction-enumeration.md)