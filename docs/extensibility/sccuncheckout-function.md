---
description: Bu işlev, önceki bir kullanıma alma işlemini geri alarak seçilen dosyanın veya dosyaların içeriğini kullanıma alma öncesinde durumuna geri yükleme.
title: SccUncheckout İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3a382a112b5a11acc36c52735c949ebef71052ec
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904093"
---
# <a name="sccuncheckout-function"></a>SccUncheckout İşlevi
Bu işlev, önceki bir kullanıma alma işlemini geri alarak seçilen dosyanın veya dosyaların içeriğini kullanıma alma öncesinde durumuna geri yükleme. Geri almadan sonra dosyada yapılan tüm değişiklikler kaybedilir.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccUncheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Parametreler
 pvContext

[in] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[in] Kaynak denetimi eklentisinin sağladığı iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi tanıtıcısı.

 nFiles

[in] Dizide belirtilen dosya `lpFileNames` sayısı.

 lpFileNames

[in] Kullanıma almayı geri almak için gereken dosyaların tam yerel yol adları dizisi.

 fOptions

[in] Komut bayrakları (kullanılmaz).

 pvOptions

[in] Kaynak denetimi eklentisine özgü seçenekler.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Kullanıma almayı geri alma başarılı oldu.|
|SCC_E_FILENOTCONTROLLED|Seçilen dosya kaynak kodu denetimi altında değildir.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya sorun sorun nedeniyle kaynak denetim sistemine erişilirken bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_NONSPECIFICERROR|Belirtilmeyen hata. Geri alma başarılı olmadı.|
|SCC_E_NOTCHECKEDOUT|Kullanıcıda dosya kullanıma alınmış değil.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_PROJNOTOPEN|Proje kaynak denetiminden açılamadı.|
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan önce iptal edildi.|

## <a name="remarks"></a>Açıklamalar
 Bu işlemden `SCC_STATUS_CHECKEDOUT` `SCC_STATUS_MODIFIED` sonra, geri alma işleminin gerçekleştirıldığı dosyalar için ve bayraklarının her ikisi de temizlendi.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
