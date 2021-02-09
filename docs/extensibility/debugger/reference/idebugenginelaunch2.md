---
title: IDebugEngineLaunch2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e4485001341399d3830864a30b64fec24a77c5a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892729"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Program başlatmak ve sonlandırmak için bir hata ayıklama altyapısı (DE) tarafından kullanılır.

## <a name="syntax"></a>Syntax

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirim, tamamen özel bir bağlantı noktası tarafından işlenebilen bir işlemi başlatmak için özel gereksinimlere sahipse özel bir DE tarafından uygulanır. Bu genellikle bir yorumlayıcının parçası olduğunda ve hata ayıklamakta olan işlemin bir komut dosyası olması durumunda oluşur: yorumlayıcının önce başlatılması gerekir, sonra betik yüklenir ve başlatılır. Bir bağlantı noktası yorumlayıcı başlatabilir, ancak komut dosyası özel işleme gerektirebilir (bunun DE bir rolü vardır). Bu arabirim yalnızca özel bir bağlantı noktasının işleyememesi için bir program başlatmaya yönelik benzersiz gereksinimler varsa uygulanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, SDM 'nin bu arabirimi [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) arabiriminden (QueryInterface kullanarak) alması durumunda oturum hata ayıklama YÖNETICISI (SDM) tarafından çağrılır. Bu arabirim elde edilebilir ise SDM, onun özel gereksinimlere sahip olduğunu bilir ve bu arabirimi, bağlantı noktasının başlatması yerine programı başlatmak için çağırır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugEngineLaunch2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|, İle bir işlem başlatır.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|İşlem yürütmeye devam eder.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Bir işlemin sonlandırılıp sonlandırılamayacağını belirler.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Bir işlemi sonlandırır.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
