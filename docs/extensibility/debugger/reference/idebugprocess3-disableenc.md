---
title: IDebugProcess3::D isableENC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b39bb448501bacd5ab458b7e61bb1a5044bc8a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723739"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Bu yöntem, bu işlemde (ve içerdiği tüm programlar) Düzenle ve devam et özelliğini açıkça devre dışı bırakır. Özel bir bağlantı noktası sağlayıcısı her zaman döndürmelidir `E_NOTIMPL` .

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>Parametreler
`reason`\
'ndaki [Encunkullanılabilirliği Blereason](../../../extensibility/debugger/reference/encunavailablereason.md) numaralandırmasından bir değer.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür.

> [!NOTE]
> Özel bir bağlantı noktası sağlayıcısı her zaman döndürmelidir `E_NOTIMPL` .

## <a name="remarks"></a>Açıklamalar
 Bir işlem için Düzenle ve devam et devre dışı bırakıldığında, işlem yeniden başlatılarak yalnızca yeniden etkinleştirilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
