---
title: IDebugProgramProvider2::GetProviderProcessData | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e958900307f5f7915f58679709c88f80c2abfc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721833"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
Belirli bir işlemden çalışan programların listesini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetProviderProcessData(
   PROVIDER_FLAGS         Flags,
   IDebugDefaultPort2*    pPort,
   AD_PROCESS_ID          processId,
   CONST_GUID_ARRAY       EngineFilter,
   PROVIDER_PROCESS_DATA* pProcess
);
```

```csharp
int GetProviderProcessData(
   enum_PROVIDER_FLAGS     Flags,
   IDebugDefaultPort2      pPort,
   AD_PROCESS_ID           ProcessId,
   CONST_GUID_ARRAY        EngineFilter,
   PROVIDER_PROCESS_DATA[] pProcess
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
|`PFLAG_GET_PROGRAM_NODES`|Arayan, döndürülecek program düğümlerinin listesini istiyor.|

`pPort`\
[içinde] Arama işleminin devam eden bağlantı noktası.

`processId`\
[içinde] Söz konusu programı içeren işlemin kimliğini tutan [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) bir yapı.

`EngineFilter`\
[içinde] Bu işlemi hata ayıklamak için atanan hata ayıklama motorları için bir dizi GUID (bunlar, sağlanan motorların desteğine göre gerçekte döndürülen programları filtrelemek için kullanılır; motor belirtilmemişse, tüm programlar döndürülür).

`pProcess`\
[çıkış] İstenen bilgilerle doldurulmuş [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) bir yapı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem normalde bu işlemde çalışan programların listesini almak için bir işlem tarafından çağrılır. Döndürülen bilgiler [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) nesnelerinin listesidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
