---
description: Bir program sağlayıcısından elde etmek istediğiniz özellikleri belirtir.
title: PROVIDER_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_FLAGS
helpviewer_keywords:
- PROVIDER_FLAGS enumeration
ms.assetid: 8cbd2312-ed2f-4477-b192-c3f25c6098c3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 116943ce1fd85b9f4dee2dc0f1512301a900fa74
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726960"
---
# <a name="provider_flags"></a>PROVIDER_FLAGS
Bir program sağlayıcısından elde etmek istediğiniz özellikleri belirtir.

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
 Çağıran, 'den farklı bir makinede program listesi [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ister.

 `PFLAG_DEBUGGEE`\
 İşlem şu anda bu örneği tarafından hata ayıklaması [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] yapılıyor.

 `PFLAG_ATTACH_TODEBUGGEE`\
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] hata ayıklaması yapılan programa eklenmiş ancak başlatılamamış.

 `PFLAG_REASON_WATCH`\
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] olayları izliyor.

 `PFLAG_GET_PROGRAM_NODES`\
 `ProgramNodes`Çağıran, veri [yapısının PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) ister.

 `PFLAG_GET_IS_DEBUGGER_PRESENT`\
 `fIsTheDebuggerPresent`Çağıran, yapının alanını `PROVIDER_PROCESS_DATA` ister.

## <a name="remarks"></a>Açıklamalar
 Bu bayraklar aşağıdaki yöntemlere geçirildi:

- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)

- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)

- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)

  Bu değerler bit olarak `OR` birleştirebilirsiniz.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
