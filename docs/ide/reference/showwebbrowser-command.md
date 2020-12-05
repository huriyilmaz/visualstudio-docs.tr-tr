---
title: ShowWebBrowser Komutu
description: Web tarayıcısını göster komutunu ve bir Web tarayıcısı penceresinde belirttiğiniz URL 'YI IDE içinde veya IDE 'nin dışında nasıl görüntülediğini öğrenin.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 026878bdc2158d803f191cf2d28c8eb52f0b6e09
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616323"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser Komutu

Bir Web tarayıcı penceresinde belirttiğiniz URL 'YI tümleşik geliştirme ortamı (IDE) veya IDE 'nin dışında görüntüler.

## <a name="syntax"></a>Söz dizimi

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Bağımsız değişkenler
`URL`

Gereklidir. Web sitesi için URL (Tekdüzen Kaynak Konum Belirleyicisi).

## <a name="switches"></a>Anahtarlar
/Yeni

İsteğe bağlı. Sayfanın, Web tarayıcısının yeni bir örneğinde göründüğünü belirtir.

/ext

İsteğe bağlı. Sayfanın IDE dışında varsayılan Web tarayıcısında göründüğünü belirtir.

## <a name="remarks"></a>Açıklamalar
**ShowWebBrowser** komutunun diğer adı **Git** veya **Gezinti**' dir.

## <a name="example"></a>Örnek
Aşağıdaki örnek, Microsoft Docs giriş sayfasını IDE dışında bir Web tarayıcısında görüntüler. Web tarayıcısının bir örneği zaten açıksa, kullanılır; Aksi halde yeni bir örnek başlatılır.

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)