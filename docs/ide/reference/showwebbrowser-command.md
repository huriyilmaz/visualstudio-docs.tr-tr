---
title: ShowWebBrowser Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8c97659cc6036433c5bcf2547a9f88aee56f451
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747721"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser Komutu

Bir Web tarayıcı penceresinde belirttiğiniz URL 'YI tümleşik geliştirme ortamı (IDE) veya IDE 'nin dışında görüntüler.

## <a name="syntax"></a>Sözdizimi

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Arguments
`URL`

Gerekli. Web sitesi için URL (Tekdüzen Kaynak Konum Belirleyicisi).

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

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)