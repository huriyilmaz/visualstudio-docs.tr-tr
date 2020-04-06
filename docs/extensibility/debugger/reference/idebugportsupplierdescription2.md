---
title: IDebugPortSupplierDescription2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69853e34788a2f24afe183dfbb7070e48f14aa46
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724362"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Kullanıcı Aracı'nın [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] **İşleme Ekle** iletişim kutusunun **Aktarım Bilgileri** bölümündeki metni görüntülemesini sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim liman tedarikçileri tarafından uygulanır.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda `IDebugPortSupplierDescription2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Bağlantı noktası tedarikçisinin açıklama ve açıklama meta verilerini alır.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll
