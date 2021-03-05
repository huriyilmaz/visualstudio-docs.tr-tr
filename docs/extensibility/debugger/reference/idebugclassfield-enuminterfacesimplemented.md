---
description: Bu sınıf tarafından uygulanan arabirimler için bir Numaralandırıcı oluşturur.
title: 'IDebugClassField:: Enumınterfacesimpted | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f90bf6efc3a34e4f6b9f60ef5bdadb0640f495b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164324"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Bu sınıf tarafından uygulanan arabirimler için bir Numaralandırıcı oluşturur.

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
dışı Uygulanan arabirimlerin listesini temsil eden bir [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür. Arabirim yoksa, null bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, bu sınıfta hiçbir arabirim uygulandıysa S_OK veya S_FALSE döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Sabit listesinin her öğesi, bir arabirimi tanımlayan bir [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) nesnesidir. Yönetilmeyen [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] kodun arabirimleri ayrık bir varlık olarak kullanmadığından, bu yöntemin yönetilmeyen kod için her zaman null bir değer döndürdüğünden emin olduğunu unutmayın [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
