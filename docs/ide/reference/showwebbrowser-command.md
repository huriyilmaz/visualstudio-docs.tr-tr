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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72747721"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser Komutu

Bir web tarayıcısı penceresinde belirttiğiniz URL'yi tümleşik geliştirme ortamında (IDE) veya IDE'nin dışında görüntüler.

## <a name="syntax"></a>Sözdizimi

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Bağımsız Değişkenler
`URL`

Gereklidir. Web sitesinin URL'si (Tek Tip Kaynak Bulucu).

## <a name="switches"></a>Anahtarlar
/yeni

İsteğe bağlı. Sayfanın web tarayıcısının yeni bir örneğinde göründüğünü belirtir.

/ext

İsteğe bağlı. Sayfanın Varsayılan Web Tarayıcısı'nda IDE dışında göründüğünü belirtir.

## <a name="remarks"></a>Açıklamalar
**ShowWebBrowser** komutu için takma arama **gezinmek** veya **gezinmek**.

## <a name="example"></a>Örnek
Aşağıdaki örnekte, Microsoft Dokümanlar ana sayfası IDE dışındaki bir web tarayıcısında görüntülenir. Web tarayıcısının bir örneği zaten açıksa, kullanılır; aksi takdirde yeni bir örnek başlatılır.

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)