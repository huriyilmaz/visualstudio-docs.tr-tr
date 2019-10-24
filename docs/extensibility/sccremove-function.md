---
title: SccRemove Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ff7299868b96aedb7cc096b4e939a0f8015aeb8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720781"
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

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 lendiği

'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.

 Nkarşıya

'ndaki @No__t_0 dizisinde belirtilen dosya sayısı.

 lpDosyaAdı

'ndaki Kaldırılacak dosyaların tam nitelikli yerel yol adları dizisi.

 lpComment açıklaması

'ndaki Kaldırılmakta olan her bir dosyaya uygulanacak yorum.

 fOptions

'ndaki Komut bayrakları (kullanılmamış).

 pvOptions

'ndaki Kaynak denetimi eklentisi özel seçenekleri.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Kaldırma başarılı oldu.|
|SCC_E_FILENOTCONTROLLED|Seçili dosya kaynak denetimi altında değil.|
|SCC_E_OPNOTSUPPORTED|Kaynak denetim sistemi bu işlemi desteklemiyor.|
|SCC_E_ISCHECKEDOUT|Bir Kullanıcı şu anda kullanıma alındığından dosya kaldırılamıyor.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmiyor.|
|SCC_E_NONSPECIFICERROR|Özel olmayan hata; dosya kaldırılmadı.|
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan önce iptal edildi.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, dosyaları kaynak denetim sisteminden kaldırır ancak kullanıcının yerel sabit sürücüsünden silmez.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)