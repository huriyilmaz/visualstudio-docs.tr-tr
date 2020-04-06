---
title: MESAJ TÜRÜ | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714494"
---
# <a name="messagetype"></a>MESSAGETYPE
İleti türünü ve nedenini belirtir.

## <a name="syntax"></a>Sözdizimi

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
 İletinin çıkış penceresine gönderilmesi gerektiğini gösterir. Bu birbirini dışlayan `MT_MESSAGEBOX`bir şey.

 `MT_MESSAGEBOX`\
 İletinin ileti kutusunda gösterilmesi gerektiğini gösterir. Bu birbirini dışlayan `MT_OUTPUTSTRING`bir şey.

 `MT_TYPE_MASK`\
 İletinin hedefini yalıtmak için bir maske değeri.

 `MT_REASON_EXCEPTION`\
 Bir özel durum sonucunda ileti kutusunun gösterildiğini gösterir. Bu birbirini dışlayan `MT_REASON_TRACEPOINT`bir şey.

 `MT_REASON_TRACEPOINT`\
 İzleme noktasına çarpması sonucu ileti kutusunun gösterildiğini gösterir. Bu birbirini dışlayan `MT_REASON_EXCEPTION`bir şey.

 `MT_REASON_MASK`\
 İletinin gösterilme nedenini yalıtmak için bir maske değeri.

## <a name="remarks"></a>Açıklamalar
 Bu değerler GetMessage ve [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) yöntemlerinden döndürülür. [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)

 Neden değerlerinden biri bitwise `OR`kullanılarak çıktı hedef değerlerinden biri ile kombine edilebilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
