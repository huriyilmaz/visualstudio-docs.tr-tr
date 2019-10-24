---
title: SccProperties Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e269727441eebc93cd78b70f11fdb571f111ee8b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720841"
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

 Özellikler kaynak denetimi eklentisi tarafından tanımlanır ve eklentilerden farklı olabilir. Eklenti, kullanıcının bir dosyanın kaynak denetimi özelliklerini değiştirmesine izin veriyorsa, bu dosya veya projenin yeniden yüklenmesi gereken IDE 'yi bildirmek için `SCC_I_RELOAD` döndürmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)