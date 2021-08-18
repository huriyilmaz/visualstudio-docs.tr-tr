---
title: Dosyalarda Bul Komutu
description: Bul komutunu ve Bul ve Değiştir penceresinin Dosyalarda Bul sekmesindeki bazı seçenekleri kullanarak dosyalarda nasıl arama yaptığı hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 3ccc2bb3a6d324d64fb2332326ae083fc84a3db6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151684"
---
# <a name="find-in-files-command"></a>Dosyalarda Bul Komutu
Bul ve Değiştir penceresinin Dosyalarda Bul sekmesinde bulunan **seçeneklerin bir** alt **kümesini kullanarak dosyaları** ara.

## <a name="syntax"></a>Söz dizimi

```cmd
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Bağımsız değişkenler

`findwhat`\
Gereklidir. Eşleşmesi gereken metin.

## <a name="switches"></a>Anahtarlar
/case veya /c\
İsteğe bağlı. Eşleşmeler yalnızca büyük ve küçük harf karakterler bağımsız değişkende belirtilenlerle tam olarak eşiliyorsa `findwhat` oluşur.

/ext: `extensions`\
İsteğe bağlı. Aranacak dosyaların dosya uzantılarını belirtir. Belirtilmezse, daha önce girilmemişse önceki uzantı kullanılır.

/lookin: `searchpath`\
İsteğe bağlı. Aranan dizin. Yol boşluk içeriyorsa, yolun tamamını tırnak işaretleri içine alın.

/names veya /n\
İsteğe bağlı. Eşleşmeleri içeren dosya adlarının listesini görüntüler.

/options veya /t\
İsteğe bağlı. Geçerli bul seçeneği ayarlarının listesini görüntüler ve arama gerçekleştirmez.

/regex veya /r\
İsteğe bağlı. Bağımsız değişkende, değişmez karakter yerine metin desenlerini temsil eden `findwhat` notlarda önceden tanımlanmış özel karakterleri kullanır. Normal ifade karakterlerinin tam listesi için bkz. [Normal İfadeler.](../../ide/using-regular-expressions-in-visual-studio.md)

/reset veya /e\
İsteğe bağlı. Varsayılan ayarlarına bulma seçeneklerini döndürür ve arama gerçekleştirmez.

/stop\
İsteğe bağlı. Devam eden bir arama işlemi varsa geçerli arama işlemi durdurulr. Arama, belirtilen diğer tüm bağımsız `/stop` değişkenleri yoksayıyor. Örneğin, geçerli aramayı durdurmak için şunları girersiniz:

```cmd
>Edit.FindinFiles /stop
```

/sub veya /s\
İsteğe bağlı. /lookin: bağımsız değişkensinde belirtilen dizin içindeki alt klasörleri `searchpath` arar.

/text2 veya /2\
İsteğe bağlı. Sonuçları Bul 2 penceresinde aramanın sonuçlarını görüntüler.

/wild veya /l\
İsteğe bağlı. Bir karakteri veya karakter dizisini temsil `findwhat` etmek için, bağımsız değişkende önceden tanımlanmış özel karakterleri not olarak kullanır.

/word veya /w\
İsteğe bağlı. Yalnızca tam sözcükleri arar.

## <a name="example"></a>Örnek
Bu örnek, "My Visual Studio Projects" klasöründe bulunan tüm .cls dosyalarında btnCancel'i arar ve Sonuçları Bul 2 Penceresinde eşleşme bilgilerini görüntüler.

```cmd
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>Ayrıca bkz.

- [Dosyalarda Bul](../../ide/find-in-files.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
