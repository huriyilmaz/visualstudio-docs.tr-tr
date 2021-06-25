---
description: Bu işlev, bir dosya veya projenin kaynak denetimi özelliklerini görüntüler.
title: SccProperties İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cd50353ab29c05e5e5db2dc2b3f363af46ca8aa7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904197"
---
# <a name="sccproperties-function"></a>SccProperties İşlevi
Bu işlev, bir dosya veya projenin kaynak denetimi özelliklerini görüntüler.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccProperties (
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName
);
```

#### <a name="parameters"></a>Parametreler
 pvContext

[in] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[in] Kaynak denetimi eklentisinin sağladığı iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi tanıtıcısı.

 lpFileName

[in] Dosyanın veya projenin tam yol adı.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Özellikler başarıyla görüntülendi.|
|SCC_I_RELOADFILE|Sürüm denetimi sistemi dosya özelliklerini değiştirmektedir, bu nedenle IDE bu dosyayı yeniden yüklemelidir.|
|SCC_E_PROJNOTOPEN|Belirtilen proje kaynak denetiminde açık değil.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu dosyanın veya projenin özelliklerini görüntüleme yetkisi yok.|
|SCC_E_FILENOTCONTROLLED|Belirtilen dosya veya proje kaynak denetimi altında değil.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Bilinmeyen veya genel bir hata oluştu.|

## <a name="remarks"></a>Açıklamalar
 Kaynak denetimi eklentisi, özellikleri kendi iletişim kutusunda görüntüler.

 Özellikler kaynak denetimi eklentisi tarafından tanımlanır ve eklentiden eklentiye farklılık gösterebilir. Eklenti, kullanıcının bir dosyanın kaynak denetimi özelliklerini değiştirmesini sağlarsa, IDE'ye bu dosyanın veya projenin yeniden yüklenmeye ihtiyaç olduğunu işaret etmek `SCC_I_RELOAD` için geri dönmeli.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
