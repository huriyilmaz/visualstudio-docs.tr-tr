---
description: Bu sınıf tarafından uygulanan arabirimler için bir numaralayıcı oluşturur.
title: IDebugClassField::EnumInterfacesImplemented | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8395a35a2f0e5aa7481148562dc12b66da39e257
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627482"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Bu sınıf tarafından uygulanan arabirimler için bir numaralayıcı oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumInterfacesImplemented( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumInterfacesImplemented(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametreler
`ppEnum`\
[out] Uygulanan [arabirimlerin listesini temsil eden bir IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür. Arabirim yoksa null değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK veya S_FALSE arabirim uygulanmamışsa bu işlevi döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Numaralamanın her öğesi, arabirimini açıklayan [bir IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) nesnesidir. Unmanaged code'un arabirimleri ayrık varlık olarak kullanmaz, bu nedenle bu yöntem her zaman, unmanaged code için [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] null değer [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
