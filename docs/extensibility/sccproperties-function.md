---
title: SccProperties Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf2dd87efbb50346093144db6e069eea30138e37
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700503"
---
# <a name="sccproperties-function"></a>SccProperties İşlevi
Bu işlev, bir dosya veya proje için kaynak denetim özelliklerini görüntüler.

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

[içinde] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[içinde] Kaynak denetim eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresine bir tanıtıcı.

 lpFileName

[içinde] Dosyanın veya projenin tam nitelikli yol adı.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Özellikler başarıyla görüntülendi.|
|SCC_I_RELOADFILE|Sürüm denetim sistemi dosya özelliklerini değiştirmiştir, bu nedenle IDE bu dosyayı yeniden yüklemelidir.|
|SCC_E_PROJNOTOPEN|Belirtilen proje kaynak denetiminde açılmadı.|
|SCC_E_NOTAUTHORIZED|Kullanıcı, bu dosyanın veya projenin özelliklerini görüntüleme yetkisine sahip değildir.|
|SCC_E_FILENOTCONTROLLED|Belirtilen dosya veya proje kaynak denetimi altında değildir.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Bilinmeyen veya genel bir hata oluştu.|

## <a name="remarks"></a>Açıklamalar
 Kaynak denetimi eklentisi özellikleri kendi iletişim kutusunda görüntüler.

 Özellikler kaynak kontrol eklentisi tarafından tanımlanır ve eklentiden eklentiye farklılık gösterebilir. Eklenti, kullanıcının bir dosyanın kaynak denetim özelliklerini değiştirmesine izin `SCC_I_RELOAD` veriyorsa, Bu dosyanın veya projenin yeniden yüklenmesi gerektiğini IDE sinyalivermek için geri dönmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
