---
description: bu arabirim, hata ayıklama altyapısı tarafından sağlanan kaynak belgedeki değişiklikler hakkında Visual Studio bildirmek için kullanılır.
title: IDebugDocumentTextEvents2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 1a90cd9ae5fa9e43a12a7b023f807aaf16ceef58
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119210"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
bu arabirim, hata ayıklama altyapısı tarafından sağlanan kaynak belgedeki değişiklikler hakkında Visual Studio bildirmek için kullanılır.

## <a name="syntax"></a>Syntax

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirim, kaynak kodda değişiklik yapmayı desteklemek için DE uygular. Bu arabirim, genellikle [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) arabirimini uygulayan aynı nesneye uygulanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Bu arabirimi yöntemine bir çağrı aracılığıyla edinir <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> . <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>Arabirim, yöntemine yapılan çağrıdan alınır <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> . <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>Arabirim, bir [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) arabiriminde [QueryInterface](/cpp/atl/queryinterface) yöntemi çağırarak elde edilir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugDocumentTextEvents2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Tüm belgenin yok edildiğini belirtir.|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Hata ayıklama paketine metin eklenmiş olduğunu bildirir.|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Hata ayıklama paketine metnin belgeden kaldırıldığını bildirir.|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Hata ayıklama paketine metnin belgede değiştirildiğini bildirir.|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Hata ayıklama paketine metin özniteliklerinin güncelleştirildiğini bildirir.|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Belge özniteliklerinin güncelleştirildiğini olayı alıcıya bildirir.|

## <a name="remarks"></a>Açıklamalar
 Yalnızca kendi belgelerini sağlayan hata ayıklama motorları arabiriminden faydalanabilir `IDebugDocumentTextEvent2` . Bunun bir örneği, bir komut dosyası hata ayıklama altyapısı olacaktır. Betikleri yorumlama sürecinde, hiçbir disk dosyasında bulunmayan ve yalnızca DE ' de bilinen yeni kaynak kodu oluşturulabilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
