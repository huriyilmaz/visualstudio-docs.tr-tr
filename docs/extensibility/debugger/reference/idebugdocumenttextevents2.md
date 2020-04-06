---
title: IDebugDocumentTextEvents2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44a1736890ac78e7aaf20b4a639b1794fc63b5ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731372"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Bu arabirim, hata ayıklama altyapısı tarafından sağlanan kaynak belgede yapılan değişiklikler hakkında Visual Studio'yu bilgilendirmek için kullanılır.

## <a name="syntax"></a>Sözdizimi

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, kaynak kodda değişiklik yapmayı desteklemek için bu arabirimi uygular. Bu arabirim genellikle [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) arabirimini uygulayan aynı nesne üzerinde uygulanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> yönteme bir çağrı yoluyla bu arabirimi elde eder. Arabirim, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> yönteme yapılan <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> bir çağrıdan elde edilir. Arabirim, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) arabiriminde [QueryInterface](/cpp/atl/queryinterface) yöntemini arayarak elde edilir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugDocumentTextEvents2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Belgenin tamamının yok edildiğini gösterir.|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Hata ayıklama paketinin belgeye metin eklendiğini bildirin.|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Hata ayıklama paketine metnin belgeden kaldırıldığını bildirin.|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Hata ayıklama paketine belgede metnin değiştirildiğini bildirin.|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Hata ayıklama paketine metin özniteliklerinin belgede güncelleştirildiğini bildirin.|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Belge özniteliklerinin güncelleştirildiğini alıcıya bildirimde eder.|

## <a name="remarks"></a>Açıklamalar
 Yalnızca kendi belgelerini sağlayan hata ayıklama `IDebugDocumentTextEvent2` motorları arabirimden yararlanır. Bunun bir örneği bir komut dosyası hata ayıklama altyapısı olacaktır. Komut dosyalarını yorumlama sürecinde, herhangi bir disk dosyasında bulunmayan ve yalnızca DE tarafından bilinen yeni kaynak kodu oluşturulabilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
