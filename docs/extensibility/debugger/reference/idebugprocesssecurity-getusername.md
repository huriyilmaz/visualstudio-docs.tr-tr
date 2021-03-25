---
description: Bağlantı noktası tedarikçiden Kullanıcı adını alır.
title: 'Idebugprocesssecurity:: GetUserName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42a13075b233d5b0fe70b314a4b2d025a2a4c7d3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076309"
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
