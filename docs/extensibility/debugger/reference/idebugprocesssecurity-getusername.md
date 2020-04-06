---
title: IDebugProcessSecurity::GetUserName | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef00a0b7489c3e5cb709520546f3d3f26c8a4eba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723250"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Kullanıcı adını bağlantı noktası tedarikçisinden alır.

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
[çıkış] Kullanıcı adını içeren bir dize.

## <a name="return-value"></a>Dönüş Değeri
 Yöntem başarılı olursa, döndürür. `S_OK` Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 `GetUserName`**İşleme Ekle** iletişim kutusunun **Kullanıcı Adı** sütununda görüntülenen kullanıcı adını döndürür. **İşleme Ekle** iletişim kutusunu görüntülemek [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] için, tümleşik geliştirme ortamında (IDE) **Araçlar** menüsünde **İşleme Ekle'yi** tıklatın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
