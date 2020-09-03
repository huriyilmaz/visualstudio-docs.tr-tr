---
title: 'IDebugProgramProvider2:: GetProviderProcessData | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721833"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
Belirli bir işlemden çalışan programların bir listesini alır.

## <a name="syntax"></a>Söz dizimi

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
'ndaki [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) numaralandırmasındaki bayrakların birleşimi. Aşağıdaki bayraklar bu çağrı için tipik olarak verilmiştir:

|Bayrak|Açıklama|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Çağıran uzak makinede çalışıyor.|
|`PFLAG_DEBUGGEE`|Çağıranın Şu anda hata ayıklaması yapılıyor (her düğüm için sıralama ile ilgili ek bilgiler döndürülecek).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Çağıran, hata ayıklayıcı tarafından eklenmiş ancak başlatılmamış.|
|`PFLAG_GET_PROGRAM_NODES`|Arayan program düğümlerinin bir listesini döndürülmesini istiyor.|

`pPort`\
'ndaki Çağıran işlemin üzerinde çalıştığı bağlantı noktası.

`processId`\
'ndaki Söz konusu programı içeren işlemin KIMLIĞINI tutan bir [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) yapısı.

`EngineFilter`\
'ndaki Bu işlemde hata ayıklamak için atanan hata ayıklama altyapılarının GUID dizisi (Bunlar, sağlanan altyapıların ne kadar destek olduğuna göre gerçekten döndürülen programları filtrelemek için kullanılır; hiçbir altyapı belirtilmemişse, tüm programlar döndürülür).

`pProcess`\
dışı İstenen bilgilerle doldurulmuş bir [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) yapısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, normalde bu işlemde çalışan programların listesini almak için bir işlem tarafından çağırılır. Döndürülen bilgi, [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) nesnelerinin bir listesidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
