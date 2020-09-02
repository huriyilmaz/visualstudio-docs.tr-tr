---
title: MESSAGETYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4d0fd12495a59427500c16ef6f37d9f8b6e61f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714494"
---
# <a name="messagetype"></a>MESSAGETYPE
İleti türünü ve nedenini belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
typedef DWORD MESSAGETYPE;
```

```csharp
public enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
```

## <a name="fields"></a>Alanlar
 `MT_OUTPUTSTRING`\
 İletinin çıkış penceresine gönderilmesi gerektiğini gösterir. Bu, öğesinden birbirini dışlıyor `MT_MESSAGEBOX` .

 `MT_MESSAGEBOX`\
 İletinin bir ileti kutusunda gösterilmesi gerektiğini gösterir. Bu, öğesinden birbirini dışlıyor `MT_OUTPUTSTRING` .

 `MT_TYPE_MASK`\
 İleti hedefini yalıtmak için bir maske değeri.

 `MT_REASON_EXCEPTION`\
 Bir özel durumun sonucu olarak ileti kutusu gösterilmekte olduğunu gösterir. Bu, öğesinden birbirini dışlıyor `MT_REASON_TRACEPOINT` .

 `MT_REASON_TRACEPOINT`\
 Bir izleme noktasına vurmaktan kaynaklanan bir ileti kutusunun gösterilmekte olduğunu gösterir. Bu, için birbirini dışlar `MT_REASON_EXCEPTION` .

 `MT_REASON_MASK`\
 Gösterilen ileti nedenini yalıtmak için bir maske değeri.

## <a name="remarks"></a>Açıklamalar
 Bu değerler [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) ve [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) yöntemlerinden döndürülür.

 Neden değerlerinden biri, bit düzeyinde kullanılan çıkış hedefi değerlerinden biri ile birleştirilebilir `OR` .

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
