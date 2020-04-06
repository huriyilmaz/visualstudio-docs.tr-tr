---
title: SccRunScc Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d012908e59be8b82e34ff68cdab1945c5bd2de8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700401"
---
# <a name="sccrunscc-function"></a>SccRunScc İşlevi
Bu işlev kaynak denetim yönetim aracını çağırır.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccRunScc(
   LPVOID  pvContext,
   HWND    hWnd,
   LONG    nFiles,
   LPCSTR* lpFileNames
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

[içinde] Seçili dosya adlarının dizilimi.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Kaynak denetimi yönetim aracı başarıyla çağrıldı.|
|SCC_I_OPERATIONCANCELED|İşlem iptal edildi.|
|SCC_E_INITIALIZEFAILED|Kaynak kontrol sistemini başlatmada başarısız oldu.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişmede büyük olasılıkla ağ veya çekişme sorunları nedeniyle bir sorun vardı.|
|SCC_E_CONNECTIONFAILURE|Kaynak kontrol sistemine bağlanılamamış.|
|SCC_E_FILENOTCONTROLLED|Seçili dosya kaynak denetimi altında değil.|
|SCC_E_NONSPECIFICERROR|Nonspesifik bir hata.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, arayanın dış yönetim aracı aracılığıyla kaynak denetim sisteminin tüm özelliklerine erişmesine olanak tanır. Kaynak denetim sisteminin kullanıcı arabirimi yoksa, kaynak denetim eklentisi gerekli yönetim işlevlerini gerçekleştirmek için bir arabirim uygulayabilir.

 Bu işlev, şu anda seçili dosyalar için bir sayı ve dosya adları dizisi yle birlikte çağrılır. Yönetim aracı destekliyorsa, dosya listesi yönetim arabirimindeki dosyaları önceden seçmek için kullanılabilir; aksi takdirde, liste yoksayılabilir.

 Bu işlev genellikle kullanıcı **Dosya** -> Kaynağı**Denetimi** menüsünden **>Başlat \<Kaynak Denetim Sunucusu'nu** seçtiğinde çağrılır. Bu **Başlat** menüsü seçeneği, bir kayıt defteri girişi ayarlayarak her zaman devre dışı bırakılmış veya hatta gizlenebilir. Bkz. Nasıl Yapılacağını ZİYEŞFİ: Ayrıntılar için [Kaynak Denetimi Eklentisi yükleyin.](../extensibility/internals/how-to-install-a-source-control-plug-in.md) Bu işlev yalnızca [SccInitialize](../extensibility/sccinitialize-function.md) yetenek `SCC_CAP_RUNSCC` bitini döndürürse çağrılır (bu ve diğer yetenek bitleri hakkındaki ayrıntılar için [Yetenek Bayrakları'na](../extensibility/capability-flags.md) bakın).

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Nasıl Yapılır: Kaynak Denetimi Eklentisi Yükleme](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Özellik Bayrakları](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
