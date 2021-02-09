---
title: IEnumDebugPrograms2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 04566b4a8dae7f25f799d08780c93936009adef8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890753"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Bu arabirim, geçerli hata ayıklama oturumunda çalışan programları numaralandırır.

## <a name="syntax"></a>Syntax

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), bu arabirimi, ' DE hata ayıklamakta olan programların bir listesini sağlamak için uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Visual Studio bu arabirimi edinmek için [Enumprograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) 'ı çağırır. [Enumprograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) , Visual Studio tarafından kullanılmaz.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IEnumDebugPrograms2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Bir numaralandırma dizisindeki belirtilen sayıda programı alır.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Bir numaralandırma dizisinde belirtilen sayıda programı atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Bir numaralandırma dizisini başlangıca sıfırlar.|
|[Oluşturulacak](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Bir Numaralandırıcı içindeki program sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio bu arabirimi şu amaçlarla kullanır:

- **Modüller** penceresini doldurun ( [enumprograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) çağırarak ve ardından her programda [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) çağırarak).

- **Işleme İliştir** listesini doldurun ( `IDebugProcess2::EnumPrograms` bir [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) arabirimi edinmek için her [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabiriminde [QueryInterface](/cpp/atl/queryinterface) 'i çağırarak ve sonra çağırarak).

- İşlemdeki her programda hata ayıklayabilmesi gereken DEs listesini oluşturun ( [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)kullanarak).

- Her programa Düzenle ve devam et (ENC) güncelleştirmelerini Uygula (IDebugProcess2:: EnumPrograms çağırarak ve sonra [Getencupdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)'i çağırarak).

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
