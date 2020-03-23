---
title: Seçenekler, Metin Düzenleyici, JavaScript, IntelliSense
ms.date: 10/29/2018
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.IntelliSense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3d030e028332bd57afe66eee31c888713721212
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68605974"
---
# <a name="options-dialog-box-text-editor--javascript--intellisense"></a>Seçenekler iletişim kutusu: \> Metin \> DüzenleyicijavaScript IntelliSense

JavaScript için **IntelliSense'in** davranışını etkileyen ayarları değiştirmek için **Seçenekler** iletişim kutusunun IntelliSense sayfasını kullanın. Menü çubuğunda **Araç** > **Seçenekleri'ni** seçip **Metin DüzenleyicijavaScript/TypeScript** > **JavaScript/TypeScript** > **IntelliSense'i** genişleterek **IntelliSense** sayfasına erişebilirsiniz.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

**IntelliSense** sayfası aşağıdaki bölümleri içerir:

## <a name="statement-completion"></a>Deyim Tamamlama

IntelliSense deyim tamamlama davranışını değiştirmek için bu seçenekleri kullanabilirsiniz.

### <a name="uielement-list"></a>UIElement listesi

**Yalnızca Işlemek için Sekme veya Enter'u kullanın**

Bu onay kutusunu seçtiğinizde, JavaScript kod düzenleyicisi, yalnızca **Sekme** veya **Enter** tuşunu seçtikten sonra tamamlama listesinde seçilen öğelerle ifadeleri ekler. Bu onay kutusunu n için ilerlettiğinizde, nokta, virgül, üst üste, açık parantez ve açık ayraç ({) gibi diğer karakterler de seçili öğelerle deyimleri ekleyebilir.

## <a name="references"></a>Başvurular

Farklı JavaScript projesi türleri için kapsamda olan IntelliSense .js türlerini belirtmek için bu seçenekleri kullanabilirsiniz. IntelliSense başvuruları normalde, genel nesneler için IntelliSense desteği sağlamak amacıyla kullanılır. Bu sayfayı, çalışma zamanında yüklenmesi gereken komut dosyalarının yüklenme sırasını ayarlamak ve IntelliSense uzantı dosyalarını eklemek için de kullanabilirsiniz.

### <a name="uielement-list"></a>UIElement listesi

**Referans grupları**

Bu seçenek başvuru grubu türünü belirtir. Üç başvuru grubu desteklenir:

Belirli IntelliSense .js dosyalarının farklı JavaScript projeleri için kapsamda olduğunu belirtmek için önceden tanımlı başvuru gruplarını kullanabilirsiniz. Dört başvuru grubu mevcuttur:

- Örtülü (Windows *sürümü),* JavaScript kullanan uygulamalar için. [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] Bu gruba dahil olan dosyalar, JavaScript kullanan uygulamalar için Kod [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] Düzenleyicisi'nde açılan her .js dosyası için kapsamdadır.

- Örtük (Web); HTML5 projeleri için. Bu grupta yer alan dosyalar, bu proje türleri için Kod Düzenleyicisi'nde açılan her .js dosyası için kapsama girer.

- HTML5 web çalışanları için özel işçi başvuru grupları. Bu grupta belirtilen dosyalar, bir adanmış çalışan başvuru grubuna dair açık başvuru içeren .js dosyaları için kapsama girer.

- Genel; diğer JavaScript proje türleri için.

**Dahil edilen dosyalar**

Bu seçenek, dil hizmetinin bağlamına dosyaların yüklendiği sırayı belirtir. **Kaldır**, **Yukarı Taşı**ve Aşağı **Taşı** düğmelerini kullanarak siparişi yapılandırabilirsiniz. IntelliSense'in düzgün çalışması için, bir diğer dosyaya bağımlı olan dosya söz konusu bu diğer dosyadan sonra yüklenmelidir.

> [!CAUTION]
> Bir nesne iki veya daha fazla örtük başvuruda koşulsuz olarak tanımlanırsa, nesneyi tanımlamak için bu listedeki son başvuru kullanılır.

**Gruba referans ekleme**

Bu seçenek, uygun dosyaların bulunduğu yere giderek ek IntelliSense .js dosyalarını eklemek için bir yol sağlar.

**Çeşitli dosyalar projesindeki dosyalar için uzaktan referansları (örn. http://) indirin**

Bu onay kutusu seçildiğinde ve bir proje bağlamı dışında açılmış bir JavaScript dosyanız varsa, Visual Studio IntelliSense bilgilerini sağlamak amacıyla dosyada başvurulan uzak JavaScript dosyalarını indirir. Bu seçenek seçilirse, Dosyalar JavaScript dosyanıza referans olarak eklediğinizde karşıdan yüklenir.

> [!NOTE]
> Web projeleri için, projenizde başvurulan uzak dosyalar varsayılan olarak karşıdan yüklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [JavaScript IntelliSense](../../ide/javascript-intellisense.md)