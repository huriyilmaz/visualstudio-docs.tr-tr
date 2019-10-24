---
title: SccUncheckout Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e35d7287d8fc12100da9ba3b8383d8e92cee73d4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720527"
---
# <a name="sccuncheckout-function"></a>SccUncheckout İşlevi
Bu işlev önceki bir kullanıma alma işlemini geri alır ve böylece seçilen dosya veya dosyaların içeriğini kullanıma almadan önceki duruma geri yükler. Kullanıma alma işleminden bu yana dosyada yapılan tüm değişiklikler kayboldu.

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

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 lendiği

'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.

 Nkarşıya

'ndaki @No__t_0 dizisinde belirtilen dosya sayısı.

 lpDosyaAdı

'ndaki Bir kullanıma alma işlemini geri almak için gereken dosyaların tam nitelikli yerel yol adları dizisi.

 fOptions

'ndaki Komut bayrakları (kullanılmıyor).

 pvOptions

'ndaki Kaynak denetimi eklentisi özel seçenekleri.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Kullanıma alma başarıyla geri alındı.|
|SCC_E_FILENOTCONTROLLED|Seçili dosya kaynak kodu denetimi altında değil.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu. Yeniden deneme önerilir.|
|SCC_E_NONSPECIFICERROR|Özel olmayan hata. Kullanıma alma başarıyla geri alınamıyor.|
|SCC_E_NOTCHECKEDOUT|Kullanıcının dosyası kullanıma alınmamış.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmiyor.|
|SCC_E_PROJNOTOPEN|Proje, kaynak denetiminden açılmamış.|
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan önce iptal edildi.|

## <a name="remarks"></a>Açıklamalar
 Bu işlemden sonra, `SCC_STATUS_CHECKEDOUT` ve `SCC_STATUS_MODIFIED` bayrakları, geri alma işleminin gerçekleştirildiği dosyalar için temizlenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)