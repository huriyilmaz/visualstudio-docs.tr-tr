---
title: SccUncheckout Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4317133b2f215e0f9af447e5c042785561231f63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700243"
---
# <a name="sccuncheckout-function"></a>SccUncheckout İşlevi
Bu işlev, önceki bir ödeme işlemini geri alarak, seçili dosya veya dosyaların içeriğini ödemeden önce duruma geri getirir. Ödeme kaybolduğundan beri dosyada yapılan tüm değişiklikler.

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

[içinde] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[içinde] Kaynak denetim eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresine bir tanıtıcı.

 nDosyalar

[içinde] `lpFileNames` Dizide belirtilen dosya sayısı.

 lpFileNames

[içinde] Ödemeyi geri almak için dosyaların tam nitelikli yerel yol adlarını dizilimi.

 fSeçenekler

[içinde] Komut bayrakları (kullanılmaz).

 pvOptions

[içinde] Kaynak denetimi eklentisi özel seçenekleri.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Geri ödeme başarılı oldu.|
|SCC_E_FILENOTCONTROLLED|Seçili dosya kaynak kodu denetimi altında değildir.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişmede büyük olasılıkla ağ veya çekişme sorunları nedeniyle bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_NONSPECIFICERROR|Nonspesifik bir hata. Geri ödeme başarılı olmadı.|
|SCC_E_NOTCHECKEDOUT|Kullanıcı dosyayı kullanıma almaz.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_PROJNOTOPEN|Proje kaynak denetiminden açılmadı.|
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan iptal edildi.|

## <a name="remarks"></a>Açıklamalar
 Bu işlemden `SCC_STATUS_CHECKEDOUT` sonra, geri ödemenin gerçekleştirildiği dosyalar için bayraklar ve `SCC_STATUS_MODIFIED` bayraklar temizlenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
