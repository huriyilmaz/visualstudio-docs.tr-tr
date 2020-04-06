---
title: IDebugEngineLaunch2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee77cbd680df2c851d53aac298605023227fa6f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730497"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Programları başlatmak ve sonlandırmak için hata ayıklama altyapısı (DE) tarafından kullanılır.

## <a name="syntax"></a>Sözdizimi

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim, özel bir bağlantı noktası tarafından tamamen işlenemeyen bir işlemi başlatmak için özel gereksinimleri varsa, özel bir DE tarafından uygulanır. Bu genellikle DE bir yorumlayıcının parçası olduğunda ve debugged işlemi bir komut dosyası dır: önce yorumlayıcı başlatılması gerekir ve sonra komut dosyası yüklenir ve başlatılır. Bir bağlantı noktası yorumlayıcıyı başlatabilir, ancak komut dosyası özel kullanım gerektirebilir (DE'nin bir rolü vardır). Bu arabirim, yalnızca özel bir bağlantı noktasının işleyemeyeceği bir programı başlatmak için benzersiz gereksinimler varsa uygulanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 SDM bu arabirimi [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) arabiriminden (QueryInterface kullanarak) alabiliyorsa, bu arabirim oturum hata ayıklama yöneticisi (SDM) tarafından çağrılır. Bu arabirim elde edilebilirse, SDM DE'nin özel gereksinimleri olduğunu bilir ve bu arabirimi bağlantı noktasının başlatılması yerine programı başlatmak için çağırır.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugEngineLaunch2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|DE ile bir işlem başlatir.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|İşlem yürütmeyi devam ettirer.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Bir işlemin sonlandırılap sonlandırılamayacağını belirler.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Bir işlemi sonlandırır.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
