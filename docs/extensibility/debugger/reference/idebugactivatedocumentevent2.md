---
title: IDebugActivateDocumentEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f601027ce9e71dff6687bcd6aa1b08f13f5ce0cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736622"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
Hata ayıklama altyapısı (DE) yüklenecek bir belge istemek için bu arabirimi kullanır.

## <a name="syntax"></a>Sözdizimi

```
IDebugActivateDocumentEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, açılacak bir kaynak dosyagerektiğinde bu arabirimi uygular. Bu arabirim yalnızca komut dosyası yorumlayıcılarıyla çalışan veya bunların bir parçası olan hata ayıklama motorları tarafından uygulanır. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır (SDM `IDebugEvent2` [arabirime](/cpp/atl/queryinterface) erişmek için QueryInterface'i kullanır).

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, bir kaynak dosyasının açılması gerektiğinde bu olay nesnesini oluşturur ve gönderir. Olay, sdm tarafından sağlanan [iDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevi kullanılarak, programa eklendiğinde debugged olarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugActivateDocumentEvent2`.

|Yöntemler|Açıklama|
|-------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|Belgenin etkinleştirilmesini alır.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Belge içindeki konumu açıklayan belge bağlamını alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirimin kullanıldığı tipik bir senaryo, html sayfasındaki komut dosyası kodunda ayrıştırıcı hatası oluşursa, de komut dosyası bu arabirimi SDM'ye gönderir, böylece ayrıştırıcı hatası olan belge görüntülenebilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
