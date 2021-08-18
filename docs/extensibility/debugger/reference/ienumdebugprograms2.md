---
description: Bu arabirim, geçerli hata ayıklama oturumunda çalışan programları numaralar.
title: IEnumDebugPrograms2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 3ff57a503094e018e65bdf9913c48cb3abc9f9c1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034817"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Bu arabirim, geçerli hata ayıklama oturumunda çalışan programları numaralar.

## <a name="syntax"></a>Syntax

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), DE tarafından hata ayıklaması yapılan programların listesini sağlamak için bu arabirimi uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Visual Studio [arabirimi almak için EnumPrograms'a](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) çağrır. [EnumPrograms,](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) bir Visual Studio.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IEnumDebugPrograms2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Bir numaralama dizisinde belirtilen sayıda programı alma.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Bir numaralama dizisinde belirtilen sayıda programı atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Bir numaralama dizisini en başta sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Geçerli numaralayıcıyla aynı numaralama durumunu içeren bir numaralayıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Numaralayıcıda program sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio aşağıdakiler için bu arabirimi kullanır:

- Modüller **penceresini** (EnumPrograms'ı [çağırarak ve](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) ardından her programda [EnumModules'u](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) çağırarak) doldurmak.

- İşleme Ekle **listesini** (IDebugEngineProgram2 arabirimini almak için her `IDebugProcess2::EnumPrograms` [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabiriminde [queryInterface](/cpp/atl/queryinterface) çağırarak) ekleyin. [](../../../extensibility/debugger/reference/idebugengineprogram2.md)

- İşlemde her bir programda hata ayıklayabilen DE'ler listesi oluşturma [(GetEngineInfo kullanarak).](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)

- Her programa Düzenle ve Devam (ENC) güncelleştirmelerini uygula (IDebugProcess2::EnumPrograms çağrısı ve [ardından GetENCUpdate çağırarak).](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
