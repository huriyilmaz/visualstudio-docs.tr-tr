---
description: Hata ayıklama altyapısı (DE), bir belgenin yüklenmek için bu arabirimi kullanır.
title: IDebugActivateDocumentEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 2e2e1e516774f1acfe4041c58b97e4892aefd242
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104488"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
Hata ayıklama altyapısı (DE), bir belgenin yüklenmek için bu arabirimi kullanır.

## <a name="syntax"></a>Syntax

```
IDebugActivateDocumentEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, bir kaynak dosyanın açılmasını gerekli olduğunda bu arabirimi uygulamaya almaktadır. Bu arabirim yalnızca betik yorumlayıcılarının bir parçası olan veya ile birlikte çalışmakta olan hata ayıklama altyapıları tarafından uygulanır. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanarak (SDM, arabirime erişmek için [QueryInterface](/cpp/atl/queryinterface) `IDebugEvent2` kullanır).

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, bir kaynak dosyanın açılmasını gerektirse bu olay nesnesini oluşturur ve gönderir. Olay, hata ayıklaması yapılan programa ekli olduğunda SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri çağırma işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugActivateDocumentEvent2` gösterir.

|Yöntemler|Açıklama|
|-------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|Etkinleştirilen belgeyi alır.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Belge içindeki konumu açıklayan belge bağlamını alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirimin kullandığı tipik bir senaryo, BIR HTML sayfasındaki betik kodunda ayrıştırma hatası oluşursa, DE betiği bu arabirimi SDM'ye gönderir ve böylece ayrıştırma hatasına sahip belge görüntülenebilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
