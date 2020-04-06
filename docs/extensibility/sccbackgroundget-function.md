---
title: SccBackgroundGet Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c07076b6e257bd5519d19f841797fbc652f0c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701239"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet fonksiyonu
Bu işlev, kullanıcı etkileşimi olmadan belirtilen dosyaların her birinden kaynak denetiminden alır.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccBackgroundGet(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LONG    dwFlags,
   LONG    dwBackgroundOperationID
);
```

### <a name="parameters"></a>Parametreler
 Pcontext

[içinde] Kaynak denetimi eklentibağlam işaretçisi.

 nDosyalar

[içinde] `lpFileNames` Dizide belirtilen dosya sayısı.

 lpFileNames

[içinde, dışarı] Alınacak dosyaların addizilimi.

> [!NOTE]
> Adlar tam nitelikli yerel dosya adları olmalıdır.

 Dwflags

[içinde] Komut bayrakları`SCC_GET_ALL` `SCC_GET_RECURSIVE`( , ).

 dwBackgroundOperationID

[içinde] Bu işlemle ilişkili benzersiz bir değer.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|İşlem başarıyla tamamlandı.|
|SCC_E_BACKGROUNDGETINPROGRESS|Bir arka plan alma işlemi zaten devam etmektedir (kaynak denetimi eklentisi yalnızca eşzamanlı toplu işoperasyonlarını desteklemiyorsa bunu döndürmelidir).|
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan önce iptal edildi.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev her zaman kaynak denetim eklentisini yükleyen iş parçacığından farklı olarak çağrılır. Bu işlevin yapılana kadar dönmesi beklenmez; ancak, hepsi aynı anda birden çok dosya listesiyle birden çok kez çağrılabilir.

 `dwFlags` Bağımsız değişkenin kullanımı [SccGet](../extensibility/sccget-function.md)ile aynıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi API fonksiyonları](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
