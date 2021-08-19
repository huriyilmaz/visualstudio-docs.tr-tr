---
description: Meta veri içeri aktarma bilgilerini alır.
title: 'Idebugsymbolproviderdirect:: Getmetadataımport | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetMetaDataImport
- IDebugSymbolProviderDirect::GetMetaDataImport
ms.assetid: b51a492c-af00-4b08-93fb-6c19ee4916aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 504ad9f7d995376e5e7bd848fb9cdb983cddce20
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132463"
---
# <a name="idebugsymbolproviderdirectgetmetadataimport"></a>IDebugSymbolProviderDirect::GetMetaDataImport
Meta veri içeri aktarma bilgilerini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetMetaDataImport (
    GUID*      guid,
    DWORD      appID,
    IUnknown** ppImport
);
```

```csharp
int GetMetaDataImport (
    Guid       guid,
    uint       appID,
    out object ppImport
);
```

## <a name="parameters"></a>Parametreler
`guid`\
'ndaki Modül için benzersiz tanımlayıcı.

`appID`\
'ndaki Uygulama etki alanı için tanımlayıcı.

`ppImport`\
dışı Meta veri içeri aktarma bilgilerini içeren bir nesne döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
