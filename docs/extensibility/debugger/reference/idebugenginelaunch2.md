---
description: Program başlatmak ve sonlandırmak için bir hata ayıklama altyapısı (DE) tarafından kullanılır.
title: IDebugEngineLaunch2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a8931590ea20373b5350d880d5fe9495dfe53c4f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077388"
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
