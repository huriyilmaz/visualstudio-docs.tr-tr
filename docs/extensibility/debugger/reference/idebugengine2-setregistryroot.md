---
description: Hata ayıklama altyapısı (DE) için kayıt defteri kökünü ayarlar.
title: 'IDebugEngine2:: SetRegistryRoot | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetRegistryRoot
helpviewer_keywords:
- IDebugEngine2::SetRegistryRoot
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d2e5d8f9fc435740d536c4bcd33c270763c0be8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035195"
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
Hata ayıklama altyapısı (DE) için kayıt defteri kökünü ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetRegistryRoot( 
   LPCOLESTR pszRegistryRoot
);
```

```csharp
int SetRegistryRoot( 
   string pszRegistryRoot
);
```

## <a name="parameters"></a>Parametreler
`pszRegistryRoot`\
'ndaki Kullanılacak kayıt defteri kökü.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ' ın kayıt defteri ayarlarını almak için kullanması gereken alternatif bir kayıt defteri kökü belirlemesine izin verir; örneğin, "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp".

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
