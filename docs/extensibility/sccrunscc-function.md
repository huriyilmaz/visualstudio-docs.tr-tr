---
description: Bu işlev kaynak denetimi yönetim aracını çağırır.
title: SccRunScc İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 277bfe2aa6c49a8d93307ce93d46b6fff6156f4f9c4fc008f6e5bb8e25212a6d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121413953"
---
# <a name="sccrunscc-function"></a>SccRunScc İşlevi
Bu işlev kaynak denetimi yönetim aracını çağırır.

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

[in] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[in] Kaynak denetimi eklentisinin sağladığı iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi tanıtıcısı.

 nFiles

[in] Dizide belirtilen dosya `lpFileNames` sayısı.

 lpFileNames

[in] Seçilen dosya adlarının dizisi.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini geri dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Kaynak denetimi yönetim aracı başarıyla çağrıldı.|
|SCC_I_OPERATIONCANCELED|İşlem iptal edildi.|
|SCC_E_INITIALIZEFAILED|Kaynak denetim sistemi başlatılamadı.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişirken büyük olasılıkla ağ veya iletişim sorunları nedeniyle bir sorun vardı.|
|SCC_E_CONNECTIONFAILURE|Kaynak denetim sistemine bağlanılamadı.|
|SCC_E_FILENOTCONTROLLED|Seçilen dosya kaynak denetimi altında değil.|
|SCC_E_NONSPECIFICERROR|Belirtilmeyen hata.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, çağıranın bir dış yönetim aracı aracılığıyla kaynak denetim sisteminin tüm özelliklerine erişmesini sağlar. Kaynak denetim sisteminin kullanıcı arabirimi yoksa, kaynak denetim eklentisi gerekli yönetim işlevlerini gerçekleştirmek için bir arabirim gerçekleştirebilirsiniz.

 Bu işlev, şu anda seçili olan dosyalar için bir sayı ve bir dizi dosya adı ile çağrılır. Yönetim aracı destekliyorsa, yönetim arabiriminde dosyaların ön seçimi için dosya listesi kullanılabilir; aksi takdirde liste yoksayılabilir.

 Bu işlev genellikle kullanıcı Dosya Kaynağı Denetimi menüsünden **\<Source Control Server> Başlat'ı**   ->  **seçerse çağrılır.** Bu **Başlat** menü seçeneği her zaman devre dışı bırakılabilir, hatta bir kayıt defteri girişi ayar tarafından gizlenir. Ayrıntılar [için bkz. Kaynak Denetimi Eklentisi](../extensibility/internals/how-to-install-a-source-control-plug-in.md) Yükleme. Bu işlev yalnızca [SccInitialize](../extensibility/sccinitialize-function.md) yetenek bitini döndürecekse çağrılır (bu ve diğer yetenek bitleri hakkında ayrıntılı bilgi için bkz. Yetenek `SCC_CAP_RUNSCC` Bayrakları). [](../extensibility/capability-flags.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Nasıl Yapılır: Kaynak Denetimi Eklentisi Yükleme](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Özellik Bayrakları](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
