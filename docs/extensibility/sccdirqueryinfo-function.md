---
title: SccDirQueryInfo Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 222b5d15a1e2bcd9bd3f27a5cd0e9904642d9786
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700947"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo fonksiyonu
Bu işlev, geçerli durumları için tam nitelikli dizinlerin listesini inceler.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccDirQueryInfo(
LPVOID  pContext,
LONG    nDirs,
LPCSTR* lpDirNames,
LPLONG  lpStatus
);
```

### <a name="parameters"></a>Parametreler
 Pcontext

[içinde] Kaynak denetimi eklentisi bağlam yapısı.

 nDirs

[içinde] Sorgulanacak dizin sayısı.

 lpDirNames

[içinde] Sorgulanacak dizinlerin tam nitelikli yolları dizisi.

 lpDurum

[içinde, dışarı] Durum bayraklarını döndürmek için kaynak denetim eklentisi için bir dizi yapısı (ayrıntılar için [Dizin durum koduna](../extensibility/directory-status-code-enumerator.md) bakın).

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Sorgu başarılı oldu.|
|SCC_E_OPNOTSUPPORTED|Kaynak kodu denetim sistemi bu işlemi desteklemez.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişmede büyük olasılıkla ağ veya çekişme sorunları nedeniyle bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nonspesifik bir hata.|

## <a name="remarks"></a>Açıklamalar
 İşlev, geri dönüş dizisini `SCC_DIRSTATUS` aileden gelen bit maskesiyle doldurur (bkz. [Dizin durum kodu),](../extensibility/directory-status-code-enumerator.md)verilen her dizin için bir giriş. Durum dizisi arayan tarafından ayrılır.

 Dizin, ilgili bir projeye sahip olup olmadığını sorgulayarak dizinin kaynak denetimi altında olup olmadığını denetlemek için dizin yeniden adlandırılmadan önce Bu işlevi kullanır. Dizin kaynak denetimi altında değilse, IDE kullanıcıya uygun uyarı sağlayabilir.

> [!NOTE]
> Kaynak denetim eklentisi durum değerlerinden birini veya birkaçını uygulamamayı seçerse, uygulanmamış bitler sıfıra ayarlanmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi API fonksiyonları](../extensibility/source-control-plug-in-api-functions.md)
- [Dizin durum kodu](../extensibility/directory-status-code-enumerator.md)
