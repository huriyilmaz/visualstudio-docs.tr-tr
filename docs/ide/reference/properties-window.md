---
description: Düzenleyicilerde ve tasarımcılarda bulunan seçili nesnelerin tasarım zamanı özelliklerini ve olaylarını görüntülemek ve değiştirmek için bu pencereyi kullanın.
title: Özellikler Penceresi
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- properties [Visual Studio], Properties Window
- handler functions, Properties window
- handlers, Properties window
- Windows messages
- properties [Visual Studio], setting at design time
- properties [Visual Studio], editing
- Property Browser
- Windows messages, adding message handlers
- Properties window, overrides
- virtual functions, Properties window
- Properties window
ms.assetid: e6e0fa4f-75c4-4a52-af15-281cd61876ca
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ddbfb4d001f73e30296a35c2cff4aae0e0c527f9
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221125"
---
# <a name="properties-window"></a>Özellik penceresi

Düzenleyicilerde ve tasarımcılarda bulunan seçili nesnelerin tasarım zamanı özelliklerini ve olaylarını görüntülemek ve değiştirmek için bu pencereyi kullanın. Ayrıca, dosya, proje ve çözüm özelliklerini düzenlemek ve görüntülemek için **Özellikler** penceresini de kullanabilirsiniz. **Özellikler** penceresini **Görünüm** menüsünde bulabilirsiniz. Ayrıca, **F4** tuşuna basarak veya arama kutusuna **Özellikler** yazarak da açabilirsiniz.

**Özellikler** penceresi, belirli bir özelliğin ihtiyaçlarına bağlı olarak farklı türlerde Düzenle alanları görüntüler. Bu düzenleme alanları, düzenleme kutularını, açılan listeleri ve özel Düzenleyici iletişim kutularına bağlantıları içerir. Gri renkte gösterilen özellikler salt okunurdur.

## <a name="uielement-list"></a>UIElement Listesi

Nesne adı \
Şu anda seçili olan nesneyi veya nesneleri listeler. Yalnızca etkin düzenleyici veya tasarımcı nesneleri görünür. Birden çok nesne seçtiğinizde yalnızca seçili tüm nesneler için ortak olan özellikler görünür.

Sınıflandır
Seçili nesne için tüm özellikleri ve özellik değerlerini kategoriye göre listeler. Görünür özelliklerin sayısını azaltmak için bir kategoriyi daraltabilirsiniz. Bir kategoriyi genişlettikten veya daralttığınızda, kategori adının solunda bir artı (+) veya eksi (-) görürsünüz. Kategoriler alfabetik olarak listelenir.

Göre
Alfabetik olarak, seçilen nesneler için tüm tasarım zamanı özelliklerini ve olaylarını sıralar. Soluk olmayan bir özelliği düzenlemek için, sağ tarafındaki hücreyi tıklatın ve değişiklikleri girin.

Özellik sayfaları \
Seçili öğe için **Özellik sayfaları** iletişim kutusunu veya **Proje Tasarımcısı** ' nı görüntüler. Özellik sayfaları, **Özellikler** penceresinde kullanılabilen özelliklerin bir alt kümesini, aynısını veya bir üst kümesini görüntüler. Projenizin etkin yapılandırmasıyla ilgili özellikleri görüntülemek ve düzenlemek için bu düğmeyi kullanın.

Özelliklerinin
Bir nesnenin özelliklerini görüntüler. Birçok nesnenin aynı zamanda **Özellikler** penceresi kullanılarak görüntülenebilen olayları vardır.

Özellik kaynağına göre sırala \
Devralma, uygulanan stiller ve bağlamalar gibi, kaynağa göre özellikleri gruplandırır. Yalnızca tasarımcıda XAML dosyaları düzenlenirken kullanılabilir.

Olayları
Bir nesne için olayları görüntüler.

> [!NOTE]
> Bu **Özellikler** penceresi araç çubuğu denetimi yalnızca bir form veya denetim Tasarımcısı bir proje bağlamında etkin olduğunda kullanılabilir [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] . XAML dosyaları düzenlenirken, olaylar Özellikler penceresinin ayrı bir sekmesinde görünür.

İletilerine
Tüm Windows iletilerini listeler. Seçili sınıf için belirtilen işlemler için belirtilen işleyici işlevlerini eklemenize veya silmesine izin verir.

> [!NOTE]
> Bu **Özellikler** penceresi araç çubuğu denetimi yalnızca **sınıf görünümü** bir proje bağlamında etkin pencere olduğunda kullanılabilir [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .

Kılma
Seçilen sınıf için tüm sanal işlevleri listeler ve geçersiz kılma işlevlerini eklemenize veya kaldırmanıza olanak sağlar.

> [!NOTE]
> Bu **Özellikler** penceresi araç çubuğu denetimi yalnızca **sınıf görünümü** bir proje bağlamında etkin pencere olduğunda kullanılabilir [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .

Açıklama bölmesi \
Özelliğin türünü ve kısa bir açıklamasını gösterir. Özelliğin açıklamasını, kısayol menüsünde Açıklama komutunu kullanarak ve üzerinde açabilirsiniz.

> [!NOTE]
> Bu **Özellikler** penceresi araç çubuğu denetimi, tasarımcıda XAML dosyaları düzenlenirken kullanılamaz.

Küçük resim görünümü \
Tasarımcıda XAML dosyaları düzenlenirken Şu anda seçili olan öğenin görsel temsilini gösterir.

Aramanız
Tasarımcıda XAML dosyaları düzenlenirken Özellikler ve olaylar için bir arama işlevi sağlar. Arama kutusu, siz yazarken kısmi sözcük aramalarına ve güncelleştirmelerin arama sonuçlarına yanıt verir.

## <a name="see-also"></a>Ayrıca bkz.

- [Proje Özellikleri Başvurusu](../../ide/reference/project-properties-reference.md)
- [Pencere düzenlerini özelleştirme](../../ide/customizing-window-layouts-in-visual-studio.md)
