---
description: Bu işlev, kaynak denetim sisteminden dosyaları siler.
title: SccRemove İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6c15323e98f0427016c0d6fa7353cb38d5a301b9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062673"
---
# <a name="sccremove-function"></a>SccRemove İşlevi
Bu işlev, kaynak denetim sisteminden dosyaları siler.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccRemove(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
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

[in] Kaldırılacak dosyaların tam yerel yol adları dizisi.

 lpComment

[in] Kaldırılan her dosyaya uygulanacak açıklama.

 fOptions

[in] Komut bayrakları (kullanılmayan).

 pvOptions

[in] Kaynak denetimi eklentisine özgü seçenekler.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini geri dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Kaldırma başarılı oldu.|
|SCC_E_FILENOTCONTROLLED|Seçilen dosya kaynak denetimi altında değil.|
|SCC_E_OPNOTSUPPORTED|Kaynak denetim sistemi bu işlemi desteklemez.|
|SCC_E_ISCHECKEDOUT|Kullanıcı şu anda dosyayı kullanıma alınmış olduğundan dosya kaldıramıyor.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişirken büyük olasılıkla ağ veya iletişim sorunları nedeniyle bir sorun vardı.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_NONSPECIFICERROR|Belirtilmeyen hata; dosyası kaldırılamadı.|
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan önce iptal edildi.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev dosyaları kaynak denetim sisteminden kaldırır ancak kullanıcının yerel sabit sürücüsünden silemez.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
