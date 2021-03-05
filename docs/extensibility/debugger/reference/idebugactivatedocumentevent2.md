---
description: Hata ayıklama altyapısı (DE), yüklenecek bir belge istemek için bu arabirimi kullanır.
title: IDebugActivateDocumentEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 557cb86765c06c8589f30a013a1087764f3f909e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145462"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
Hata ayıklama altyapısı (DE), yüklenecek bir belge istemek için bu arabirimi kullanır.

## <a name="syntax"></a>Syntax

```
IDebugActivateDocumentEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Ayrıca, bu arabirimi açılacak kaynak dosyasına ihtiyaç duyduğunda uygular. Bu arabirim yalnızca ile çalışan veya betik yorumlayıcılarının bir parçası olan hata ayıklama motorları tarafından uygulanır. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde UYGULANMALıDıR (SDM, arabirime erişmek için [QueryInterface](/cpp/atl/queryinterface) kullanır `IDebugEvent2` ).

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Ayrıca, bir kaynak dosyası açılması gerektiğinde bu olay nesnesini oluşturur ve gönderir. Olay, hata ayıklamakta olan programa eklendiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugActivateDocumentEvent2` .

|Yöntemler|Açıklama|
|-------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|Etkinleştirilecek belgeyi alır.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Belge içindeki konumu açıklayan belge bağlamını alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirimin kullanıldığı tipik bir senaryo, bir HTML sayfasındaki betik kodunda ayrıştırma hatası oluşursa, komut dosyası da bu arabirimi SDM 'ye gönderir, böylece ayrıştırma hatası olan belge görüntülenir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
