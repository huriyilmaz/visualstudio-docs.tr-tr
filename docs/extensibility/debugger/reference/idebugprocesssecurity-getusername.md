---
description: Bağlantı noktası sağlayıcıdan kullanıcı adını alır.
title: IDebugProcessSecurity::GetUserName | Microsoft Docs
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
ms.openlocfilehash: 025e6d4b707280ee00cd262cb917ab30c47298835e0d881faa000c049796a0fd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121451776"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Bağlantı noktası sağlayıcıdan kullanıcı adını alır.

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
[out] Kullanıcı adını içeren bir dize.

## <a name="return-value"></a>Dönüş Değeri
 Yöntem başarılı olursa `S_OK` döndürür. Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 `GetUserName` , İşleme Ekle iletişim kutusunun **Kullanıcı Adı** sütununda görüntülenen kullanıcı **adını** döndürür. İşleme Ekle **iletişim kutusunu görüntülemek** için tümleşik geliştirme  ortamındaki (IDE) Araçlar menüsünde İşleme  [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Ekle'ye tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
