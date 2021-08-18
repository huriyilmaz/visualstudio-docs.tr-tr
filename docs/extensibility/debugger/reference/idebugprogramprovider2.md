---
description: Bu kayıtlı arabirim, oturum hata ayıklama yöneticisinin (SDM) IDebugProgramPublisher2 arabirimi aracılığıyla yayımlanan programlar hakkında bilgi edinmasına olanak sağlar.
title: IDebugProgramProvider2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 44eca905c761fceae02f879f8891098f9d6932c9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050526"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
Bu kayıtlı arabirim, oturum hata ayıklama yöneticisinin (SDM) [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) arabirimi aracılığıyla "yayımlanmış" programlar hakkında bilgi edinmasına olanak sağlar.

## <a name="syntax"></a>Syntax

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
Hata ayıklama altyapısı (DE), hata ayıklama yapılan programlar hakkında bilgi sağlamak için bu arabirimi uygulamaya almaktadır. Bu arabirim, Hata Ayıklama için SDK Yardımcıları bölümünde açıklandığı gibi ölçümü kullanılarak kayıt defterinin DE `metricProgramProvider` [bölümüne kaydedilir.](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
KAYıT defterinden alınan program sağlayıcısının ile COM `CoCreateInstance` `CLSID` işlevini çağırma. Bkz. Örnek.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler

|Yöntem|Açıklama|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Çalışan programlar hakkında çeşitli yollarla filtrelenmiş bilgiler elde edilir.|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Belirli bir işlem kimliği verilen bir program düğümünü alır.|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Belirli işlem türleriyle ilişkili sağlayıcı olaylarını izlemek için bir geri arama sağlar.|
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|DE tarafından gereken dile özgü kaynaklar için yerel bir yerel seçim sağlar.|

## <a name="remarks"></a>Açıklamalar
Normalde bir işlem, bu işlemde çalışan programları bulmak için bu arabirimi kullanır.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

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
