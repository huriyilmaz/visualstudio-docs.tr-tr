---
description: Veri akışına göre hata ayıklama sembollerini yükler.
title: IDebugComPlusSymbolProvider::LoadSymbolsFromStream | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::LoadSymbolsFromStream
- LoadSymbolsFromStream
ms.assetid: 1de272f0-24f4-4548-8b70-a205cddd4727
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52edc2569044b39411677d36c235791cd41c58e0c907baeade1556ecc28e0901
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121342433"
---
# <a name="idebugcomplussymbolproviderloadsymbolsfromstream"></a>IDebugComPlusSymbolProvider::LoadSymbolsFromStream
Veri akışına göre hata ayıklama sembollerini yükler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT LoadSymbolsFromStream(
    ULONG32   ulAppDomainID,
    GUID      guidModule,
    ULONGLONG baseAddress,
    IUnknown* pUnkMetadataImport,
    IStream*  pStream
);
```

```csharp
int LoadSymbolsFromStream(
    uint    ulAppDomainID,
    Guid    guidModule,
    ulong   baseAddress,
    object  pUnkMetadataImport,
    IStream pStream
);
```

## <a name="parameters"></a>Parametreler
`ulAppDomainID`\
[in] Uygulama etki alanının tanımlayıcısı.

`guidModule`\
[in] Modülün benzersiz tanımlayıcısı.

`baseAddress`\
[in] Temel bellek adresi.

`pUnkMetadataImport`\
[in] Sembol meta verilerini içeren nesne.

`pStream`\
[in] Sembolleri içeren veri akışı.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="example"></a>Örnek
Aşağıdaki örnek, **IDebugComPlusSymbolProvider** arabirimini ortaya çıkaran [bir CDebugSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) nesnesi için bu yöntemin nasıl uygulandığını gösterir. yöntemi [LoadSymbolsFromStreamWithCorModule yöntemini](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md) çağırıyor.

```cpp
HRESULT CDebugSymbolProvider::LoadSymbolsFromStream(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    ULONGLONG baseOffset,
    IUnknown* pUnkMetadataImport,
    IStream* pStream
)
{
    return LoadSymbolsFromStreamWithCorModule (ulAppDomainID, guidModule, baseOffset, pUnkMetadataImport, NULL, pStream);
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
