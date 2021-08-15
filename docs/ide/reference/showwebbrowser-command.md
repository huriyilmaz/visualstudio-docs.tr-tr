---
title: ShowWebBrowser Komutu
description: Web Tarayıcısını Göster komutunu ve belirttiğiniz URL'yi IDE içinde veya IDE'nin dışında bir web tarayıcısı penceresinde nasıl görüntüley olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 05c51b422f187fd2302e998f95568393a6bcf5c1bb530336885f0192a092b4d1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121303806"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser Komutu

Web tarayıcısı penceresinde belirttiğiniz URL'yi tümleşik geliştirme ortamında (IDE) veya IDE'nin dışında görüntüler.

## <a name="syntax"></a>Söz dizimi

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Bağımsız değişkenler
`URL`

Gereklidir. Web sitesinin URL'si (Tekdüz Kaynak Bulucu).

## <a name="switches"></a>Anahtarlar
/new

İsteğe bağlı. Sayfanın web tarayıcısının yeni bir örneğinde görüntülendiğinden belirtir.

/ext

İsteğe bağlı. Sayfanın IDE'nin dışındaki varsayılan web tarayıcısında görüntülendiğinden belirtir.

## <a name="remarks"></a>Açıklamalar
**ShowWebBrowser komutunun diğer adı** gezinti veya **gezintidir.** 

## <a name="example"></a>Örnek
Aşağıdaki örnekte IDE Microsoft Docs bir web tarayıcısında giriş sayfası görüntülenir. Web tarayıcısının bir örneği zaten açıksa kullanılır; aksi takdirde yeni bir örnek başlatıldı.

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)