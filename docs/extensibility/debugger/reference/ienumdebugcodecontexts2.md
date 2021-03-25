---
description: Bu arabirim, hata ayıklama oturumuyla ilişkili kod bağlamlarını veya belirli bir program veya belgeyi sıralar.
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
ms.workload:
- vssdk
ms.openlocfilehash: 72addd1bd5a71f8d6051d1a7100d2d34dab57a24
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086579"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Bu arabirim, hata ayıklama oturumuyla ilişkili kod bağlamlarını veya belirli bir program veya belgeyi sıralar.

## <a name="syntax"></a>Syntax

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), bir programdaki belirli bir metin konumu için kod bağlamlarının listesini ya da belirli bir belge bağlamı için kod bağlamlarının listesini göstermek üzere bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bir programın kaynak belgesindeki belirli bir metin konumu için kod bağlamlarının bir listesini temsil eden bu arabirimi almak için [Enumcodebağlamlarını](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) çağırın.

 Belirli bir kaynak belgedeki tüm kod bağlamlarının listesini temsil eden bu arabirimi almak için [Enumcodebağlamlarını](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) çağırın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IEnumDebugCodeContexts2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Sabit Listesi dizisinde belirtilen sayıda kod bağlamı alır.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Sabit Listesi dizisinde belirtilen sayıda kod bağlamlarını atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Bir numaralandırma dizisini başlangıca sıfırlar.|
|[Oluşturulacak](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Bir Numaralandırıcı içindeki kod bağlamlarının sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio, kullanıcının bir sonraki ifadeyi ayarlarken veya bir kaynak dosya için ayrıştırılmış kodu göstererek bir kod bağlamlarının listesini doldurmak için [Enumcodebağlamlarını](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) çağırır. Birden çok kod bağlamı oluşabilir, örneğin, C++ stilinde bir şablonun birden çok örneği olduğunda.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
