---
description: Bu işlev, belirtilen dosyaların her birini Kullanıcı etkileşimi olmadan kaynak denetiminden alır.
title: SccBackgroundGet Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4df0866458f04081c82796767808194b292866a1
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220930"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet işlevi
Bu işlev, belirtilen dosyaların her birini Kullanıcı etkileşimi olmadan kaynak denetiminden alır.

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
 pContext

'ndaki Kaynak denetimi eklentisi bağlam işaretçisi.

 Nkarşıya

'ndaki Dizide belirtilen dosya sayısı `lpFileNames` .

 lpDosyaAdı

[in, out] Alınacak dosyaların adları dizisi.

> [!NOTE]
> Adların tam yerel dosya adları olması gerekir.

 dwFlags

'ndaki Komut bayrakları ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 dwBackgroundOperationID

'ndaki Bu işlemle ilişkili benzersiz bir değer.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|İşlem başarıyla tamamlandı.|
|SCC_E_BACKGROUNDGETINPROGRESS|Bir arka plan alımı zaten devam ediyor (kaynak denetimi eklentisi bunu yalnızca eşzamanlı Batch işlemlerini desteklemiyorsa döndürmelidir).|
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan önce iptal edildi.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev her zaman, kaynak denetimi eklentisini yükleyen bilgisayardan farklı bir iş parçacığında çağrılır. Bu işlevin, tamamlanana kadar dönmesi beklenmez; Ancak, hepsi aynı anda birden çok dosya listesiyle birden çok kez çağrılabilir.

 `dwFlags`Bağımsız değişkeninin kullanımı [SccGet](../extensibility/sccget-function.md)ile aynıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
