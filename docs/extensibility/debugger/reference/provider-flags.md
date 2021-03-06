---
description: Bir program sağlayıcısından elde edilecek istenen özellikleri belirtir.
title: PROVIDER_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_FLAGS
helpviewer_keywords:
- PROVIDER_FLAGS enumeration
ms.assetid: 8cbd2312-ed2f-4477-b192-c3f25c6098c3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8851dffa0de1155edf401c0d0b0feadda199a5e9
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222035"
---
# <a name="provider_flags"></a>PROVIDER_FLAGS
Bir program sağlayıcısından elde edilecek istenen özellikleri belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PROVIDER_FLAGS {
   PFLAG_NONE                    = 0x00,
   PFLAG_REMOTE_PORT             = 0x01,
   PFLAG_DEBUGGEE                = 0x02,
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,
   PFLAG_REASON_WATCH            = 0x08,
   PFLAG_GET_PROGRAM_NODES       = 0x10,
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20
};
typedef DWORD PROVIDER_FLAGS;
```

```csharp
public enum enum_PROVIDER_FLAGS {
   PFLAG_NONE                    = 0x00,
   PFLAG_REMOTE_PORT             = 0x01,
   PFLAG_DEBUGGEE                = 0x02,
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,
   PFLAG_REASON_WATCH            = 0x08,
   PFLAG_GET_PROGRAM_NODES       = 0x10,
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20
};
```

## <a name="fields"></a>Alanlar
 `PFLAG_NONE`\
 Bayrak belirtilmedi.

 `PFLAG_REMOTE_PORT`\
 Çağıran, farklı bir makinede bulunan programların listesini ister [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

 `PFLAG_DEBUGGEE`\
 İşlem şu anda bu örneği tarafından ayıklanıyor [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

 `PFLAG_ATTACH_TODEBUGGEE`\
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] hata ayıklanan programa bağlı ancak başlatılamadı.

 `PFLAG_REASON_WATCH`\
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] olaylar için izliyor.

 `PFLAG_GET_PROGRAM_NODES`\
 Çağıran `ProgramNodes` [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) yapısını alan istiyor.

 `PFLAG_GET_IS_DEBUGGER_PRESENT`\
 Çağıran, `fIsTheDebuggerPresent` yapının alanını istiyor `PROVIDER_PROCESS_DATA` .

## <a name="remarks"></a>Açıklamalar
 Bu bayraklar aşağıdaki yöntemlere geçirilir:

- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)

- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)

- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)

  Bu değerler, bit düzeyinde birleştirilebilir `OR` .

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
