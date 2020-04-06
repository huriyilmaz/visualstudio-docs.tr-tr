---
title: IDebugClassField::EnumInterfacesUygulanmış | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91d9cac6b695ba2a0d34da776fa79ba62ba2e015
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734492"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Bu sınıf tarafından uygulanan arabirimler için bir sayısallaştırıcı oluşturur.

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
[çıkış] Uygulanan arabirimler listesini temsil eden bir [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür. Arabirim yoksa null değeri döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, bu sınıfta uygulanan arabirim yoksa S_FALSE S_OK döndürür veya döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Numaralandırmanın her öğesi, arabirimi açıklayan bir [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) nesnesidir. Yönetilmeyen [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] kodun arabirimleri ayrı bir varlık olarak kullanmadığını, bu nedenle bu [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] yöntemin her zaman yönetilmeyen kod için null bir değer döndürdüğüne dikkat edin.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
