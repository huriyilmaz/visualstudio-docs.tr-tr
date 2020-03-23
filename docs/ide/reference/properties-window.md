---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1be1d4fa9f1b088547bb21dfb64254209783d7e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565714"
---
# <a name="properties-window"></a>Özellik penceresi

Düzenleyiciler de ve tasarımcılarda bulunan seçili nesnelerin tasarım zamanı özelliklerini ve olaylarını görüntülemek ve değiştirmek için bu pencereyi kullanın. Dosya, proje ve çözüm özelliklerini de lemek ve görüntülemek için **Özellikler** penceresini de kullanabilirsiniz. **Görünüm** menüsünde **Özellikler** Penceresi'ni bulabilirsiniz. Ayrıca **F4** tuşuna basarak veya arama kutusuna **Özellikler** yazarak açabilirsiniz.

**Özellikler** penceresi, belirli bir özelliğin gereksinimlerine bağlı olarak farklı türde düzenleme alanları görüntüler. Bu edit alanları, özel düzenleyici iletişim kutularına bağlantılar, açılan listeler ve düzenleyicileri içerir. Gri renkle gösterilen özellikler salt okunur.

## <a name="uielement-list"></a>UIElement Listesi

Nesne adı\
Şu anda seçili nesneyi veya nesneleri listeler. Yalnızca etkin düzenleyici veya tasarımcıdan gelen nesneler görünür. Birden çok nesne seçtiğinizde, yalnızca tüm seçili nesneleriçin ortak özellikler görünür.

Kategorize edildi\
Seçili nesnenin tüm özelliklerini ve özellik değerlerini kategoriye göre listeler. Görünür özelliklerin sayısını azaltmak için bir kategoriyi daraltabilirsiniz. Bir kategoriyi genişletdiğinizde veya daralttğınızda, kategori adının solunda bir artı (+) veya eksi (-) görürsünüz. Kategoriler alfabetik olarak listelenir.

Alfabetik\
Seçili nesneler için tüm tasarım zamanı özelliklerini ve olaylarını alfabetik olarak sıralar. Küçülmemiş bir özelliği yeniden sağlamak için hücreyi sağdaki nesle tıklayın ve değişiklikleri girin.

Özellik Sayfaları\
Seçili öğe için **Özellik Sayfaları** iletişim kutusunu veya **Proje Tasarımcısını** görüntüler. Özellik Sayfaları, **Özellikler** penceresinde bulunan özelliklerin aynısı veya üst kümesi olan bir alt küme görüntüler. Projenizin etkin yapılandırması ile ilgili özellikleri görüntülemek ve düzenlemek için bu düğmeyi kullanın.

Özellikler\
Bir nesnenin özelliklerini görüntüler. Birçok nesne de **Özellikler** penceresi kullanılarak görüntülenebilir olaylar var.

Özellik Kaynağına Göre Sırala\
Devralma, uygulanan stiller ve bağlamalar gibi kaynakları göre grupları. Yalnızca tasarımcıda XAML dosyaları düzenlerken kullanılabilir.

Olaylar\
Bir nesneiçin olayları görüntüler.

> [!NOTE]
> Bu **Özellikler** penceresi araç çubuğu denetimi yalnızca bir form veya denetim [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] tasarımcısı proje bağlamında etkin olduğunda kullanılabilir. XAML dosyalarını düzenlerken, olaylar özellikler penceresinin ayrı bir sekmesinde görünür.

İletiler\
Tüm Windows iletilerini listeler. Seçili sınıf için sağlanan iletiler için belirtilen işleyici işlevlerieklemenize veya silmenize olanak tanır.

> [!NOTE]
> Bu **Özellikler** penceresi araç çubuğu denetimi yalnızca **Sınıf Görünümü** proje [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] bağlamında etkin pencere olduğunda kullanılabilir.

Geçersiz kılmalar\
Seçili sınıfın tüm sanal işlevlerini listeler ve geçersiz kılma işlevleri eklemenize veya silmenize olanak tanır.

> [!NOTE]
> Bu **Özellikler** penceresi araç çubuğu denetimi yalnızca **Sınıf Görünümü** proje [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] bağlamında etkin pencere olduğunda kullanılabilir.

Açıklama bölmesi\
Özellik türünü ve özelliğin kısa bir açıklamasını gösterir. Kısayol menüsündeki Açıklama komutunu kullanarak özelliğin açıklamasını kapatıp açabilirsiniz.

> [!NOTE]
> Bu **Özellikler** penceresi araç çubuğu denetimi, tasarımcıda XAML dosyaları düzenlerken kullanılamaz.

Küçük resim görünümü\
Tasarımcıda XAML dosyaları düzenlerken şu anda seçili öğenin görsel bir gösterimini gösterir.

Arama\
Tasarımcıda XAML dosyaları düzenlerken özellikler ve olaylar için bir Arama işlevi sağlar. Arama kutusu kısmi sözcük aramalarına yanıt verir ve siz yazarken arama sonuçlarını güncelleştirir.

## <a name="see-also"></a>Ayrıca bkz.

- [Proje Özellikleri Başvurusu](../../ide/reference/project-properties-reference.md)
- [Pencere düzenlerini özelleştirme](../../ide/customizing-window-layouts-in-visual-studio.md)
