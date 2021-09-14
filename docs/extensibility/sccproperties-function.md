---
description: Bu işlev, bir dosya veya proje için kaynak denetimi özelliklerini görüntüler.
title: SccProperties Işlevi | Microsoft Docs
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 99d83dc2cdf5dd39a6f55f39ff78a203b4ed29b0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625982"
---
# <a name="sccproperties-function"></a>SccProperties İşlevi
Bu işlev, bir dosya veya proje için kaynak denetimi özelliklerini görüntüler.

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

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 lendiği

'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.

 lpFileName

'ndaki Dosyanın veya projenin tam yol adı.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Özellikler başarıyla görüntülendi.|
|SCC_I_RELOADFILE|Sürüm denetim sistemi dosya özelliklerini değiştirdi, bu nedenle IDE 'nin bu dosyayı yeniden yüklemesi gerekir.|
|SCC_E_PROJNOTOPEN|Belirtilen proje kaynak denetiminde açılmadı.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu dosyanın veya projenin özelliklerini görüntüleme yetkisi yok.|
|SCC_E_FILENOTCONTROLLED|Belirtilen dosya veya proje kaynak denetimi altında değil.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Bilinmeyen veya genel bir hata oluştu.|

## <a name="remarks"></a>Açıklamalar
 Kaynak denetimi eklentisi, özellikleri kendi iletişim kutusunda görüntüler.

 Özellikler kaynak denetimi eklentisi tarafından tanımlanır ve eklentilerden farklı olabilir. Eklenti, kullanıcının bir dosyanın kaynak denetimi özelliklerini değiştirmesine izin veriyorsa, `SCC_I_RELOAD` Bu dosya veya projenin yeniden yüklenmesi gereken IDE 'yi işaret etmesi için döndürmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
