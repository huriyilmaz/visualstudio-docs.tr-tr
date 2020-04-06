---
title: IDebugProgramProvider2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43557e5d81e5140967a1189e57a350595d0f7220
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721696"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
Bu kayıtlı arabirim, oturum hata ayıklama yöneticisinin (SDM) [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) arabirimi üzerinden "yayınlanmış" programlar hakkında bilgi edinmesini sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
Hata ayıklama altyapısı (DE) bu arabirimi, hata ayıklanan programlar hakkında bilgi sağlamak için uygular. Bu arabirim, Hata `metricProgramProvider` [Ayıklama için SDK Yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)açıklandığı gibi, metrik kullanılarak kayıt defterinin DE bölümünde kayıtlıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Kayıt defterinden `CoCreateInstance` alınan `CLSID` program sağlayıcısıile COM işlevini arayın. Örnek'e bakın.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler

|Yöntem|Açıklama|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Çeşitli şekillerde filtrelenen, çalışan programlar hakkında bilgi alır.|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Belirli bir işlem kimliği verilen bir program düğümü alır.|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Belirli türdeki işlemlerle ilişkili sağlayıcı olaylarını izlemek için bir geri arama oluşturur.|
|[Setlocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|DE tarafından gereken dile özgü kaynaklar için bir yerel yer kurar.|

## <a name="remarks"></a>Açıklamalar
Normalde, bir işlem bu işlemde çalışan programlar hakkında bilgi edinmek için bu arabirimi kullanır.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Örnek

```cpp
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugProgramProvider2 *pProvider = NULL;
    if (pDebugEngineGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetMetric(NULL,
                    metrictypeEngine,
                    *pDebugEngineGuid,
                    metricProgramProvider,
                    &clsidProvider,
                    strRegistrationRoot);
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugProgramProvider2> spProgramProvider;
            spProgramProvider.CoCreateInstance(clsidProvider);
            if (spProgramProvider != NULL) {
                pProvider = spProgramProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [Hata Ayıklama için SDK Yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
