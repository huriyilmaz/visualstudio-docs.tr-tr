---
description: Bu arabirim, hata ayıklama oturumuyla veya belirli bir program ya da belgeyle ilişkili kod bağlamlarını numaralar.
title: IEnumDebugCodeContexts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 8b52be981dbda8bb3b73fc2596dc8988e021765d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122095627"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Bu arabirim, hata ayıklama oturumuyla veya belirli bir program ya da belgeyle ilişkili kod bağlamlarını numaralar.

## <a name="syntax"></a>Syntax

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), bir programda belirli bir metin konumu için kod bağlamlarının listesini veya belirli bir belge bağlamı için kod bağlamlarının listesini temsil etmek üzere bu arabirimi uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bir programın kaynak belgesinde belirli bir metin konumu için kod bağlamlarının listesini temsil eden bu arabirimi elde etmek için [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) çağrısı.

 Belirli bir kaynak belgede tüm kod bağlamlarının listesini temsil eden bu arabirimi elde etmek için [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) çağrısı.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IEnumDebugCodeContexts2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Bir numaralama dizisinde belirtilen sayıda kod bağlamını alan.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Bir numaralama dizisinde belirtilen sayıda kod bağlamını atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Bir numaralama dizisini en başta sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Geçerli numaralayıcıyla aynı numaralama durumunu içeren bir numaralayıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Numaralayıcıda kod bağlamlarının sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio, kullanıcının bir sonraki deyimi ayarlarken veya kaynak dosya için disassembly'yi gösterdiği kod bağlamlarının listesini doldurmak için [EnumCodeContexts'i](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) çağırır. Örneğin bir C++stili şablonun birden çok örneği olduğunda birden çok kod bağlamı oluşabilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
