---
title: SccRemove Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17889d50dbdcf68dd4cca161d6703b8b6d69ad47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700448"
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

[içinde] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[içinde] Kaynak denetim eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresine bir tanıtıcı.

 nDosyalar

[içinde] `lpFileNames` Dizide belirtilen dosya sayısı.

 lpFileNames

[içinde] Kaldırılacak dosyaların tam nitelikli yerel yol adları dizisi.

 lpYorum yap

[içinde] Kaldırılan her dosyaya uygulanacak açıklama.

 fSeçenekler

[içinde] Komut bayrakları (kullanılmayan).

 pvOptions

[içinde] Kaynak denetimi eklentisi özel seçenekleri.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Kaldırma başarılı oldu.|
|SCC_E_FILENOTCONTROLLED|Seçili dosya kaynak denetimi altında değil.|
|SCC_E_OPNOTSUPPORTED|Kaynak denetim sistemi bu işlemi desteklemez.|
|SCC_E_ISCHECKEDOUT|Bir kullanıcı şu anda kullanıma alındı çünkü bir dosya kaldıramazsınız.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişmede büyük olasılıkla ağ veya çekişme sorunları nedeniyle bir sorun vardı.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_NONSPECIFICERROR|Nonspesifik başarısızlık; dosya kaldırılmadı.|
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan iptal edildi.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev dosyaları kaynak denetim sisteminden kaldırır, ancak kullanıcının yerel sabit diskinden silmez.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
