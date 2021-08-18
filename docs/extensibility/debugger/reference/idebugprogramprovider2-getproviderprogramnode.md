---
description: Belirli bir programın program düğümünü alan.
title: IDebugProgramProvider2::GetProviderProgramNode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16de3f0cb0c7179a3fadd9fb69f10cc5f44e4840
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122096121"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Belirli bir programın program düğümünü alan.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetProviderProgramNode(
   PROVIDER_FLAGS       Flags,
   IDebugDefaultPort2*  pPort,
   AD_PROCESS_ID        processId,
   REFGUID              guidEngine,
   UINT64               programId,
   IDebugProgramNode2** ppProgramNode
);
```

```csharp
int GetProviderProgramNode(
   enum_PROVIDER_FLAGS    Flags,
   IDebugDefaultPort2     pPort,
   AD_PROCESS_ID          ProcessId,
   ref Guid               guidEngine,
   ulong                  programId,
   out IDebugProgramNode2 ppProgramNode
);
```

## <a name="parameters"></a>Parametreler
`Flags`\
[in] İlke enumerasyonundan [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) birleşimi. Bu çağrı için aşağıdaki bayraklar tipiktir:

|Bayrak|Açıklama|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Çağıran uzak makinede çalışıyor.|
|`PFLAG_DEBUGGEE`|Çağıranın şu anda hata ayıklaması yapılıyor (her düğüm için hazırlarken ek bilgiler döndürülür).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Çağıran, hata ayıklayıcısı tarafından bağlı ancak başlatıImadı.|

`pPort`\
[in] Çağırma işleminin üzerinde çalıştır olduğu bağlantı noktası.

`processId`\
[in] Söz [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) içeren işlem kimliğini tutan bir uygulama yapısı.

`guidEngine`\
[in] Programın bağlı olduğu hata ayıklama altyapısının GUID'si (varsa).

`programId`\
[in] Program düğümünü almak için programın kimliği.

`ppProgramNode`\
[out] İstenen [program düğümünü temsil eden bir IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
