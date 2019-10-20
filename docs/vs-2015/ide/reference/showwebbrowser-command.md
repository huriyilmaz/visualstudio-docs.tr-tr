---
title: ShowWebBrowser komutu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1ecf86bdc7516f05935bd944f23633b3baad2c7c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663517"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir Web tarayıcı penceresinde belirttiğiniz URL 'YI tümleşik geliştirme ortamı (IDE) veya IDE 'nin dışında görüntüler.

## <a name="syntax"></a>Sözdizimi

```
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Arguments
 `URL` gerekiyor. Web sitesi için URL (Tekdüzen Kaynak Konum Belirleyicisi).

## <a name="switches"></a>Anahtarlar
 /Yeni Isteğe bağlı. Sayfanın, Web tarayıcısının yeni bir örneğinde göründüğünü belirtir.

 /ext Isteğe bağlı. Sayfanın IDE dışında varsayılan Web tarayıcısında göründüğünü belirtir.

## <a name="remarks"></a>Açıklamalar
 **ShowWebBrowser** komutunun diğer adı **Git** veya **Gezinti**' dir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, MSDN çevrimiçi giriş sayfasını IDE dışında bir Web tarayıcısında görüntüler. Web tarayıcısının bir örneği zaten açıksa, kullanılır; Aksi halde yeni bir örnek başlatılır.

```
>View.ShowWebBrowser https://msdn.microsoft.com /ext
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
