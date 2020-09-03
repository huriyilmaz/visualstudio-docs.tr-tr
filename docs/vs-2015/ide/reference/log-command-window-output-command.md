---
title: Komut penceresi Çıkış komutunu günlüğe kaydet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9a5a29cd63f9d51f86d41d2f0f5986a77666318
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666873"
---
# <a name="log-command-window-output-command"></a>Command penceresi çıktısı günlüğü tut komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Komut** penceresinden tüm giriş ve çıkışları bir dosyaya kopyalar.

## <a name="syntax"></a>Söz dizimi

```
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Bağımsız değişkenler
 `filename` Seçim. Günlük dosyasının adı. Varsayılan olarak, dosya kullanıcının profil klasöründe oluşturulur. Dosya adı zaten varsa, günlük varolan dosyanın sonuna eklenir. Dosya belirtilmemişse, belirtilen son dosya kullanılır. Önceki bir dosya mevcut değilse, komut satırı. log adlı varsayılan bir günlük dosyası oluşturulur.

> [!TIP]
> Günlük dosyasının kaydedildiği konumu değiştirmek için, yolun herhangi bir boşluk içermesi durumunda tırnak işaretleriyle çevrelenen dosyanın tam yolunu girin.

## <a name="switches"></a>Anahtarlar
 /On Isteğe bağlı. Belirtilen dosyadaki **komut** penceresi için günlüğü başlatır ve dosyayı yeni bilgilerle ekler.

 /off Isteğe bağlı. **Komut** penceresi için günlüğü sonlandırır.

 /overwrite Isteğe bağlı. `filename`Bağımsız değişkende belirtilen dosya varolan bir dosyayla eşleşiyorsa, dosyanın üzerine yazılır.

## <a name="remarks"></a>Açıklamalar
 Dosya belirtilmemişse, komut satırı. log dosyası varsayılan olarak oluşturulur. Varsayılan olarak, bu komutun diğer adı günlüğe kaydedilir.

## <a name="examples"></a>Örnekler
 Bu örnek, yeni bir günlük dosyası oluşturur, cmdlog ve komut günlüğünü başlatır.

```
>Tools.LogCommandWindowOutput cmdlog
```

 Bu örnek günlüğe kaydetme komutlarını durduruyor.

```
>Tools.LogCommandWindowOutput /off
```

 Bu örnek, daha önce kullanılan günlük dosyasındaki komutların günlüğe kaydedilmesini sürdürür.

```
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
