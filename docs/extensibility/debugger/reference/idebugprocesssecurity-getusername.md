---
description: Bağlantı noktası tedarikçiden Kullanıcı adını alır.
title: 'Idebugprocesssecurity:: GetUserName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04ad8bf6ba572a1f9e14e26ef2ca37d021f6e3a0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166209"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Bağlantı noktası tedarikçiden Kullanıcı adını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetUserName(
    BSTR *pbstrUserName
);
```

```csharp
int GetUserName (
    string pbstrUserName
);
```

## <a name="parameters"></a>Parametreler
`pbstrUserName`\
dışı Kullanıcı adını içeren bir dize.

## <a name="return-value"></a>Dönüş Değeri
 Yöntem başarılı olursa, döndürür `S_OK` . Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 `GetUserName`**Işleme İliştir** Iletişim kutusunun **Kullanıcı adı** sütununda görüntülenen kullanıcı adını döndürür. **Işleme İliştir** iletişim kutusunu görüntülemek için tümleşik geliştirme ORTAMıNDAKI (IDE) **Araçlar** menüsünde **İşleme İliştir** ' e tıklayın [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
