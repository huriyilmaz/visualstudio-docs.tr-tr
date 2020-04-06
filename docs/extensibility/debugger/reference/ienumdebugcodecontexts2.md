---
title: IEnumDebugCodeContexts2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6917c44bb3ddc80513e7c45a6aa4ea0207fd46c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717274"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Bu arabirim, hata ayıklama oturumuyla veya belirli bir program veya belgeyle ilişkili kod bağlamlarını doğrular.

## <a name="syntax"></a>Sözdizimi

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), bir programdaki belirli bir metin konumu için kod bağlamlarının listesini veya belirli bir belge bağlamı için kod bağlamlarının listesini temsil etmek üzere bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bir programın kaynak belgesinde belirli bir metin konumu için kod bağlamlarının listesini temsil eden bu arabirimi elde etmek için [EnumCodeContexts'ı](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) arayın.

 Belirli bir kaynak belgedeki tüm kod bağlamlarının listesini temsil eden bu arabirimi elde etmek için [EnumCodeContexts'ı](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) arayın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IEnumDebugCodeContexts2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Numaralandırma sırasında belirli sayıda kod bağlamı alır.|
|[Atlamak](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Numaralandırma dizisinde belirli sayıda kod bağlamını atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Numaralandırma sırasını başa sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Geçerli numaralandırma durumuyla aynı numaralandırma durumunu içeren bir numaralandırma oluşturucu oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Bir numaralandırıcıdaki kod bağlamlarının sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio, kullanıcının bir sonraki deyimi ayarlarken veya bir kaynak dosyaiçin sökmeyi gösterirken seçebileceği kod bağlamlarının listesini doldurmak için [EnumCodeContexts'ı](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) çağırır. Örneğin, C++stili şablonunun birden çok örneği olduğunda birden çok kod bağlamı oluşabilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
