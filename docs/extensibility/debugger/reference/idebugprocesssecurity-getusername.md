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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a376a8d51d7b4d974bf0c7b609bbc53cc334cb33
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057583"
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
