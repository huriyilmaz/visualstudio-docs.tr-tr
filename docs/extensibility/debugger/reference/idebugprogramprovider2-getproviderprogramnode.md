---
title: IDebugProgramProvider2::GetProviderProgramNode | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd8ca7d5120ba20695caef2e9021ee25869df72f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721798"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Belirli bir program için program düğümlerini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetProviderProgramNode(
   PROVIDER_FLAGS       Flags,
   IDebugDefaultPort2*  pPort,
   AD_PROCESS_ID        processId,
   REFGUID              guidEngine,
   UINT64               programId,
   IDebugProgramNode2** ppProgramNode
);
```

```csharp
int GetProviderProgramNode(
   enum_PROVIDER_FLAGS    Flags,
   IDebugDefaultPort2     pPort,
   AD_PROCESS_ID          ProcessId,
   ref Guid               guidEngine,
   ulong                  programId,
   out IDebugProgramNode2 ppProgramNode
);
```

## <a name="parameters"></a>Parametreler
`Flags`\
[içinde] [numaralandırma PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) gelen bayrakların bir kombinasyonu. Aşağıdaki bayraklar bu çağrı için tipiktir:

|Bayrak|Açıklama|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Arayan uzak makinede çalışıyor.|
|`PFLAG_DEBUGGEE`|Arayan şu anda debugged ediliyor (marshalling hakkında ek bilgiler her düğüm için döndürülür).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Arayan, hata ayıklama tarafından başlatıldığı ancak başlatılmamasA da iliştirilmiş.|

`pPort`\
[içinde] Arama işleminin devam eden bağlantı noktası.

`processId`\
[içinde] Söz konusu programı içeren işlemin kimliğini tutan [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) bir yapı.

`guidEngine`\
[içinde] Programın bağlı olduğu hata ayıklama altyapısının GUID'i (varsa).

`programId`\
[içinde] Program düğümalmak için programın kimliği.

`ppProgramNode`\
[çıkış] İstenen program düğümlerini temsil eden bir [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
