---
description: Bu işlev, istemci diskteki geçerli yerel dizin ile kaynak denetimi altındaki ilgili proje arasındaki farkları görüntüler.
title: SccDirDiff İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e938cdaedf8541d787673371cfce3d07e005711f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904649"
---
# <a name="sccdirdiff-function"></a>SccDirDiff işlevi
Bu işlev, istemci diskteki geçerli yerel dizin ile kaynak denetimi altındaki ilgili proje arasındaki farkları görüntüler.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccDirDiff(
   LPVOID    pContext,
   HWND      hWnd,
   LPCSTR    lpDirName,
   LONG      dwFlags,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametreler
 Pcontext

[in] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[in] Kaynak denetimi eklentisinin sağladığı iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi tanıtıcısı.

 lpDirName

[in] Görsel bir fark göstermek için yerel dizinin tam yolu.

 Dwflags

[in] Komut bayrakları (açıklamalar bölümüne bakın).

 pvOptions

[in] Kaynak denetimi eklentisine özgü seçenekler.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Diskte dizini, kaynak kodu denetiminde projeyle aynıdır.|
|SCC_I_FILESDIFFER|Diskte dizini, kaynak kodu denetiminde projeden farklıdır.|
|SCC_I_RELOADFILE|Bir dosyanın veya projenin yeniden yüklenmiş olması gerekir.|
|SCC_E_FILENOTCONTROLLED|Dizin, kaynak kodu denetimi altında değildir.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya sorun sorun nedeniyle kaynak denetim sistemine erişilirken bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Belirtilmeyen hata.|
|SCC_E_FILENOTEXIST|Yerel dizin bulunamadı.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, kaynak denetim eklentisinde kullanıcıya belirtilen dizinde yapılan değişikliklerin listesini görüntülemesi talimatı için kullanılır. Eklenti, diskte kullanıcının dizini ile sürüm denetimi altındaki ilgili proje arasındaki farkları görüntülemek için kendi penceresini kendi tercih biçimiyle açar.

 Bir eklenti dizinlerin karşılaştırılmasını destekliyorsa, "hızlı fark" seçenekleri desteklenmiyor olsa bile dizinlerin dosya adı temelinde karşılaştırılmasını desteklemesi gerekir.

|`dwFlags`|Yorum|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|Büyük/harfe duyarsız karşılaştırma (hızlı fark veya görsel için kullanılabilir).|
|SCC_DIFF_IGNORESPACE|Boşluğu yoksayar (hızlı fark veya görsel için kullanılabilir).|
|SCC_DIFF_QD_CONTENTS|Kaynak denetimi eklentisi tarafından desteklense, dizini sessizce, bayta göre karşılar.|
|SCC_DIFF_QD_CHECKSUM|Eklenti tarafından desteklense, dizini bir sağlama listesi aracılığıyla sessizce karşılar veya desteklenmiyorsa, dizini geri SCC_DIFF_QD_CONTENTS.|
|SCC_DIFF_QD_TIME|Eklenti tarafından desteklendiyse, dizini zaman damgası aracılığıyla sessizce karşılar veya desteklenmiyorsa dizine geri SCC_DIFF_QD_CHECKSUM veya SCC_DIFF_QD_CONTENTS.|

> [!NOTE]
> Bu işlev, [SccDiff ile aynı komut bayraklarını kullanır.](../extensibility/sccdiff-function.md) Ancak, bir kaynak denetimi eklentisi dizinler için "hızlı fark" işlemi desteklemeyi seçebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
