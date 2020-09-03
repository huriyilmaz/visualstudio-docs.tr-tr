---
title: Seçenekler, metin düzenleyici, JavaScript, IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b0d9dec8ec9b3eb8860bb8b3a4ed8f7347aa54d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662230"
---
# <a name="options-text-editor-javascript-intellisense"></a>Seçenekler, Metin Düzenleyici, JavaScript, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

JavaScript için IntelliSense davranışını etkileyen ayarları değiştirmek için **Seçenekler** Iletişim kutusunun **IntelliSense** sayfasını kullanın. **IntelliSense** sayfasına, menü çubuğunda **Araçlar**, **Seçenekler** ' i ve ardından **metin Düzenleyicisi**, **JavaScript**, IntelliSense ' i genişleterek erişebilirsiniz **.**

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

 **IntelliSense** sayfası aşağıdaki bölümleri içerir:

## <a name="validation"></a>Doğrulama
 JavaScript düzenleyicisinin belgenizdeki sözdizimini doğrulama şekline ilişkin tercihleri ayarlamak için bu seçenekleri kullanabilirsiniz.

## <a name="uielement-list"></a>UIElement Listesi
 **Sözdizimi hatalarını göster** Bu onay kutusu seçili olmadığında, JavaScript kod Düzenleyicisi sözdizimi hatalarını göstermez. Kendi yazmadığınız kodla çalışıyorsanız ve sözdizimi hatalarını düzeltmeyi amaçlamıyorsanız, bu özellik kullanışlıdır.

 Bu onay kutusu seçildiğinde, **hataları uyarı olarak göster** onay kutusunu seçebilirsiniz.

 **Hataları uyarı olarak göster** Bu onay kutusu seçildiğinde, JavaScript hataları hata listesinde hatalar yerine uyarı olarak gösterilir.

 **Çeşitli dosyalar projesindeki dosyalar için Uzak başvuruları (ör. http://) İndir** Bu onay kutusu seçildiğinde ve bir proje bağlamı dışında açılmış bir JavaScript dosyanız varsa, Visual Studio IntelliSense bilgilerini sağlamak amacıyla dosyada başvurulan uzak JavaScript dosyalarını indirir. Bu seçenek işaretliyse, JavaScript dosyanıza bir başvuru olarak eklediğiniz dosyalar indirilir.

> [!NOTE]
> Web projeleri için, projenizde başvurulan uzak dosyalar varsayılan olarak indirilir.

## <a name="statement-completion"></a>Deyim Tamamlama
 IntelliSense deyim tamamlama davranışını değiştirmek için bu seçenekleri kullanabilirsiniz.

## <a name="uielement-list"></a>UIElement Listesi
 **Yalnızca Tab veya ENTER tuşlarını kullanarak işleyin** Bu onay kutusu seçildiğinde, JavaScript kod Düzenleyicisi, yalnızca sekmeyi seçtikten veya anahtarı girdikten sonra tamamlama listesinde seçilmiş öğeler içeren deyimleri ekler. Bu onay kutusu seçili olmadığında nokta, virgül, iki nokta üst üste, açılış parantezi ve açılış ayracı ({) da deyimlere seçili öğeleri ekleyebilir.

## <a name="references"></a>Başvurular
 Farklı JavaScript projesi türleri için kapsamda olan IntelliSense .js türlerini belirtmek için bu seçenekleri kullanabilirsiniz. IntelliSense başvuruları normalde, genel nesneler için IntelliSense desteği sağlamak amacıyla kullanılır. Bu sayfayı, çalışma zamanında yüklenmesi gereken komut dosyalarının yüklenme sırasını ayarlamak ve IntelliSense uzantı dosyalarını eklemek için de kullanabilirsiniz.

## <a name="uielement-list"></a>UIElement Listesi
 **Başvuru grupları** Bu seçenek, başvuru grubu türünü belirtir. Üç başvuru grubu desteklenir:

 Belirli IntelliSense .js dosyalarının farklı JavaScript projeleri için kapsamda olduğunu belirtmek için önceden tanımlı başvuru gruplarını kullanabilirsiniz. Dört başvuru grubu mevcuttur:

- JavaScript kullanan uygulamalar için örtük (Windows *sürümü*) [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] . Bu gruba eklenen dosyalar, JavaScript kullanan uygulamalar için kod Düzenleyicisi 'nde açılan her. js dosyası için kapsamdadır [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] .

- Örtük (Web); HTML5 projeleri için. Bu grupta yer alan dosyalar, bu proje türleri için Kod Düzenleyicisi'nde açılan her .js dosyası için kapsama girer.

- Adanmış çalışan başvuru grupları; HTML5 Web Çalışanları için. Bu grupta belirtilen dosyalar, bir adanmış çalışan başvuru grubuna dair açık başvuru içeren .js dosyaları için kapsama girer.

- Genel; diğer JavaScript proje türleri için.

  **Dahil edilen dosyalar** Bu seçenek, dil hizmeti bağlamına dosyaların yüklenme sırasını belirtir. Sıralamayı, **Kaldır**, **Yukarı taşı**ve **aşağı taşı** düğmelerini kullanarak yapılandırabilirsiniz. IntelliSense'in düzgün çalışması için, bir diğer dosyaya bağımlı olan dosya söz konusu bu diğer dosyadan sonra yüklenmelidir.

> [!CAUTION]
> Bir nesne iki veya daha fazla örtük başvuruda koşulsuz olarak tanımlanırsa, nesneyi tanımlamak için bu listedeki son başvuru kullanılır.

 **Gruba bir başvuru ekleyin** Bu seçenek, uygun dosyalara göz atarak ek IntelliSense. js dosyaları eklemek için bir yol sağlar.

## <a name="see-also"></a>Ayrıca Bkz.
 [JavaScript IntelliSense](../../ide/javascript-intellisense.md)
