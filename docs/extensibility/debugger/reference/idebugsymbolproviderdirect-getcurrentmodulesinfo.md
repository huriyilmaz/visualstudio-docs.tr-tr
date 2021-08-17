---
description: Sembol grubundaki modüller hakkındaki bilgileri alır.
title: 'Idebugsymbolproviderdirect:: GetCurrentModulesInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetCurrentModulesInfo
- GetCurrentModulesInfo
ms.assetid: b3b45ed2-ea4e-4389-b78a-11fc9796a6c1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b24c93e139097efe6dc12c5ddfe14c961d8d7fa91064e7cc85a4c351dded181
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121415747"
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesinfo"></a>IDebugSymbolProviderDirect::GetCurrentModulesInfo
Sembol grubundaki modüller hakkındaki bilgileri alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetCurrentModulesInfo(
   unsigned long * pCount,
   GUID *          ppGuids,
   DWORD *         pADIds,
   DWORD *         pCurrentState,
   IUnknown **     ppCDModItfs
);
```

```csharp
int GetCurrentModulesInfo(
   uint       pCount,
   Guid       ppGuids,
   uint       pADIds,
   uint       pCurrentState,
   out object ppCDModItfs
);
```

## <a name="parameters"></a>Parametreler
`pCount`\
'ndaki Dizideki modül sayısı `ppGuids` .

`ppGuids`\
'ndaki Modüller için benzersiz tanımlayıcılar içeren dizi.

`pADIds`\
'ndaki Uygulama etki alanları için tanımlayıcılar.

`pCurrentState`\
'ndaki Sembol grubunun geçerli durumu.

`ppCDModItfs`\
dışı Sembol grubundaki modülleri içeren bir nesne döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
