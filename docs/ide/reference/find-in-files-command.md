---
title: Dosyalarda Bul Komutu
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87d313c29be1d5fb4f1be1febe9b5b7cd32e7e11
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569588"
---
# <a name="find-in-files-command"></a>Dosyalarda Bul Komutu
Dosyaları Bul **ve Değiştir** penceresinin **Dosyalarda Bul** sekmesinde bulunan seçeneklerin bir alt kümesini kullanarak arama yapın.

## <a name="syntax"></a>Sözdizimi

```cmd
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Bağımsız Değişkenler

`findwhat`\
Gereklidir. Eşleşecek metin.

## <a name="switches"></a>Anahtarlar
/case veya /c\
İsteğe bağlı. Eşleşmeler yalnızca büyük ve küçük karakterler bağımsız değişkende `findwhat` belirtilenlerle tam olarak eşleşirse oluşur.

/dahili:`extensions`\
İsteğe bağlı. Aranacak dosyalar için dosya uzantılarını belirtir. Belirtilmemişse, daha önce girilmişse önceki uzantı kullanılır.

/lookin:`searchpath`\
İsteğe bağlı. Arama rehberi. Yol boşluklar içeriyorsa, tüm yolu tırnak işaretlerine biçine alıkonun.

/adlar veya /n\
İsteğe bağlı. Eşleşmeler içeren dosya adlarının listesini görüntüler.

/seçenekleri veya /t\
İsteğe bağlı. Geçerli bul seçeneği ayarlarının listesini görüntüler ve arama yapmaz.

/regex veya /r\
İsteğe bağlı. `findwhat` Bağımsız değişkende önceden tanımlanmış özel karakterleri, gerçek karakterler yerine metin desenlerini temsil eden gösterimler olarak kullanır. Normal ifade karakterlerinin tam listesi için [Normal İfadeler'e](../../ide/using-regular-expressions-in-visual-studio.md)bakın.

/sıfırlama veya /e\
İsteğe bağlı. Bul seçeneklerini varsayılan ayarlarına döndürür ve arama yapmaz.

/stop\
İsteğe bağlı. Biri devam ediyorsa geçerli arama işlemini durdurur. Arama, belirtildiğinde `/stop` diğer tüm bağımsız değişkenleri yok sayar. Örneğin, geçerli aramayı durdurmak için aşağıdakileri girersiniz:

```cmd
>Edit.FindinFiles /stop
```

/sub veya /s\
İsteğe bağlı. /lookin:`searchpath` bağımsız değişkeninde belirtilen dizindeki alt klasörleri arar.

/text2 veya /2\
İsteğe bağlı. Arama sonuçlarını Sonuçları Bul 2 penceresinde görüntüler.

/vahşi veya /l\
İsteğe bağlı. Bir karakteri veya karakter dizisini `findwhat` temsil etmek için bağımsız değişkendeki önceden tanımlanmış özel karakterleri notolarak kullanır.

/word veya /w\
İsteğe bağlı. Yalnızca tüm sözcükleri arar.

## <a name="example"></a>Örnek
Bu örnek, "Görsel Stüdyo Projelerim" klasöründe bulunan tüm .cls dosyalarında btnCancel'ı arar ve Sonuç Bul 2 Penceresinde maç bilgilerini görüntüler.

```cmd
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>Ayrıca bkz.

- [Dosyalarda Bul](../../ide/find-in-files.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
