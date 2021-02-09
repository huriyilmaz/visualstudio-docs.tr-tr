---
title: Seçenekler, Metin Düzenleyici, JavaScript, IntelliSense
description: JavaScript için IntelliSense davranışını etkileyen ayarları değiştirmek için Seçenekler iletişim kutusunun IntelliSense sayfasını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 051711a9d6dfe861f37e741ae9ecabfbf741012e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932364"
---
# <a name="options-dialog-box-text-editor--javascript--intellisense"></a>Seçenekler iletişim kutusu: metin düzenleyici \> JavaScript \> IntelliSense

JavaScript için IntelliSense davranışını etkileyen ayarları değiştirmek için **Seçenekler** Iletişim kutusunun **IntelliSense** sayfasını kullanın. **IntelliSense** sayfasına, menü çubuğunda **Araçlar**  >  **Seçenekler** ' i ve ardından **metin Düzenleyicisi**  >  **JavaScript/TypeScript** IntelliSense ' i genişleterek erişebilirsiniz  >  **.**

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

**IntelliSense** sayfası aşağıdaki bölümleri içerir:

## <a name="statement-completion"></a>Deyim Tamamlama

IntelliSense deyim tamamlama davranışını değiştirmek için bu seçenekleri kullanabilirsiniz.

### <a name="uielement-list"></a>UIElement listesi

**Yalnızca Tab veya ENTER tuşlarını kullanarak işleyin**

Bu onay kutusunu seçtiğinizde, JavaScript kod Düzenleyicisi, yalnızca **sekmeyi** seçtikten veya anahtarı **girdikten** sonra tamamlama listesinde seçilmiş öğeler içeren deyimleri ekler. Bu onay kutusunun işaretini kaldırdığınızda nokta, virgül, iki nokta, açık parantez ve açık küme ayracı ({) gibi diğer karakterler de seçili öğelerle deyimler eklenebilir.

## <a name="references"></a>Başvurular

Farklı JavaScript projesi türleri için kapsamda olan IntelliSense .js türlerini belirtmek için bu seçenekleri kullanabilirsiniz. IntelliSense başvuruları normalde, genel nesneler için IntelliSense desteği sağlamak amacıyla kullanılır. Bu sayfayı, çalışma zamanında yüklenmesi gereken komut dosyalarının yüklenme sırasını ayarlamak ve IntelliSense uzantı dosyalarını eklemek için de kullanabilirsiniz.

### <a name="uielement-list"></a>UIElement listesi

**Başvuru grupları**

Bu seçenek başvuru grubu türünü belirtir. Üç başvuru grubu desteklenir:

Belirli IntelliSense .js dosyalarının farklı JavaScript projeleri için kapsamda olduğunu belirtmek için önceden tanımlı başvuru gruplarını kullanabilirsiniz. Dört başvuru grubu mevcuttur:

- JavaScript kullanan uygulamalar için örtük (Windows *sürümü*) [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] . Bu gruba eklenen dosyalar, JavaScript kullanan uygulamalar için kod Düzenleyicisi 'nde açılan her. js dosyası için kapsamdadır [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] .

- Örtük (Web); HTML5 projeleri için. Bu grupta yer alan dosyalar, bu proje türleri için Kod Düzenleyicisi'nde açılan her .js dosyası için kapsama girer.

- HTML5 Web çalışanları için adanmış çalışan başvuru grupları. Bu grupta belirtilen dosyalar, bir adanmış çalışan başvuru grubuna dair açık başvuru içeren .js dosyaları için kapsama girer.

- Genel; diğer JavaScript proje türleri için.

**Dahil edilen dosyalar**

Bu seçenek, dil hizmetinin bağlamına dosyaların yüklendiği sırayı belirtir. Sıralamayı, **Kaldır**, **Yukarı taşı** ve **aşağı taşı** düğmelerini kullanarak yapılandırabilirsiniz. IntelliSense'in düzgün çalışması için, bir diğer dosyaya bağımlı olan dosya söz konusu bu diğer dosyadan sonra yüklenmelidir.

> [!CAUTION]
> Bir nesne iki veya daha fazla örtük başvuruda koşulsuz olarak tanımlanırsa, nesneyi tanımlamak için bu listedeki son başvuru kullanılır.

**Gruba bir başvuru ekleyin**

Bu seçenek, uygun dosyaların bulunduğu yere giderek ek IntelliSense .js dosyalarını eklemek için bir yol sağlar.

**Çeşitli dosyalar projesindeki dosyalar için Uzak başvuruları (ör. http://) İndir**

Bu onay kutusu seçildiğinde ve bir proje bağlamı dışında açılmış bir JavaScript dosyanız varsa, Visual Studio IntelliSense bilgilerini sağlamak amacıyla dosyada başvurulan uzak JavaScript dosyalarını indirir. Bu seçenek işaretliyse, JavaScript dosyanıza bir başvuru olarak dahil edildiğinde dosyalar indirilir.

> [!NOTE]
> Web projeleri için, projenizde başvurulan uzak dosyalar varsayılan olarak indirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [JavaScript IntelliSense](../../ide/javascript-intellisense.md)