---
title: Yeni Dosya Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fe8a99ee59a347fdcb7cff601b75139760630f7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595962"
---
# <a name="new-file-command"></a>Yeni Dosya Komutu
Yeni bir dosya oluşturur ve açar. Dosya Çeşitli Dosyalar klasörü altında görünür.

## <a name="syntax"></a>Sözdizimi

```cmd
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Bağımsız Değişkenler
`filename`

İsteğe bağlı. Dosyanın adı. Ad sağlanmadıysa, varsayılan ad sağlanır. Şablon adı listelenmemişse, bir metin dosyası oluşturulur.

## <a name="switches"></a>Anahtarlar
/t:`templatename`\
İsteğe bağlı. Oluşturulacak dosya türünü belirtir.

/t:`templatename` bağımsız değişken sözdizimi, Yeni Dosya İletişim Kutusu'nda bulunan bilgileri yansıtıyor. Bir ters eğik çizgi ()`\`ve şablon adı izleyen kategori adını girin ve tüm dizeyi tırnak işaretlerine bürün.

Örneğin, yeni [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] bir kaynak dosyası oluşturmak için /t:`templatename` bağımsız değişken için aşağıdakileri girersiniz.

```cmd
/t:"Visual C++\C++ File (.cpp)"
```

Yukarıdaki örnek, C++ Dosya şablonunun **Yeni Dosya** iletişim kutusunda Visual C++ kategorisinin altında bulunduğunu gösterir.

/e:`editorname`\
İsteğe bağlı. Dosyanın açılacağı düzenleyicinin adı. Bağımsız değişken belirtilir, ancak düzenleyici adı sağlanmamışsa, **Ile Aç** iletişim kutusu görüntülenir.

/e:`editorname` bağımsız değişken sözdizimi, teklif işaretleriyle birlikte açık iletişim kutusunda göründükleri gibi düzenleyici adlarını kullanır.

Örneğin, kaynak kod düzenleyicisinde bir dosya açmak için /e:`editorname` bağımsız değişkeniçin aşağıdakileri girersiniz.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Örnek
Bu örnek, "test1.htm" adlı yeni bir web sayfası oluşturur ve kaynak kod düzenleyicisinde açar.

```cmd
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Komut Penceresi](../../ide/reference/immediate-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
