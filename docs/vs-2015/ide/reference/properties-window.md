---
title: Özellikler penceresi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 959bd36995ca4086bf64020816b00aee6f777fbe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662081"
---
# <a name="properties-window"></a>Özellikler Penceresi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Düzenleyicilerde ve tasarımcılarda bulunan seçili nesnelerin tasarım zamanı özelliklerini ve olaylarını görüntülemek ve değiştirmek için bu pencereyi kullanın. Ayrıca, dosya, proje ve çözüm özelliklerini düzenlemek ve görüntülemek için **Özellikler** penceresini de kullanabilirsiniz. **Özellikler** penceresini **Görünüm** menüsünde bulabilirsiniz. Ayrıca, F4 tuşuna basarak veya **Hızlı Başlat** penceresine **Özellikler** yazarak da açabilirsiniz.

 **Özellikler** penceresi, belirli bir özelliğin ihtiyaçlarına bağlı olarak farklı türlerde Düzenle alanları görüntüler. Bu düzenleme alanları, düzenleme kutularını, açılan listeleri ve özel Düzenleyici iletişim kutularına bağlantıları içerir. Gri renkte gösterilen özellikler salt okunurdur.

## <a name="uielement-list"></a>UIElement Listesi
 Nesne adı şu anda seçili olan nesneyi veya nesneleri listeler. Yalnızca etkin düzenleyici veya tasarımcı nesneleri görünür. Birden çok nesne seçtiğinizde yalnızca seçili tüm nesneler için ortak olan özellikler görünür.

 Kategorilere ayrılmış olarak seçili nesne için tüm özellikleri ve özellik değerlerini kategorilere ayrılır. Görünür özelliklerin sayısını azaltmak için bir kategoriyi daraltabilirsiniz. Bir kategoriyi genişlettikten veya daralttığınızda, kategori adının solunda bir artı (+) veya eksi (-) görürsünüz. Kategoriler alfabetik olarak listelenir.

 Alfabetik alfabetik olarak, seçili nesneler için tüm tasarım zamanı özelliklerini ve olaylarını sıralar. Soluk olmayan bir özelliği düzenlemek için, sağ tarafındaki hücreyi tıklatın ve değişiklikleri girin.

 Özellik sayfaları, seçili öğe için **Özellik sayfaları** iletişim kutusunu veya **Proje tasarımcısını** görüntüler. Özellik sayfaları, **Özellikler** penceresinde kullanılabilen özelliklerin bir alt kümesini, aynısını veya bir üst kümesini görüntüler. Projenizin etkin yapılandırmasıyla ilgili özellikleri görüntülemek ve düzenlemek için bu düğmeyi kullanın.

 Özellikler bir nesnenin özelliklerini görüntüler. Birçok nesnenin aynı zamanda **Özellikler** penceresi kullanılarak görüntülenebilen olayları vardır.

 Özellik kaynağı, devralma, uygulanan stiller ve bağlamalar gibi kaynağa göre özelliklere göre sıralayın. Yalnızca tasarımcıda XAML dosyaları düzenlenirken kullanılabilir.

 Olaylar bir nesne için olayları görüntüler.

> [!NOTE]
> Bu **Özellikler** penceresi araç çubuğu denetimi yalnızca bir form veya denetim Tasarımcısı [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projesi bağlamında etkin olduğunda kullanılabilir. XAML dosyaları düzenlenirken, olaylar Özellikler penceresinin ayrı bir sekmesinde görünür.

 İletiler tüm Windows iletilerini listeler. Seçili sınıf için belirtilen işlemler için belirtilen işleyici işlevlerini eklemenize veya silmesine izin verir.

> [!NOTE]
> Bu **Özellikler** penceresi araç çubuğu denetimi yalnızca **sınıf görünümü** bir [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projesi bağlamında etkin pencere olduğunda kullanılabilir.

 Geçersiz kılmalar seçili sınıf için tüm sanal işlevleri listeler ve geçersiz kılma işlevlerini eklemenize veya kaldırmanıza olanak sağlar.

> [!NOTE]
> Bu **Özellikler** penceresi araç çubuğu denetimi yalnızca **sınıf görünümü** bir [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projesi bağlamında etkin pencere olduğunda kullanılabilir.

 Açıklama bölmesi Özellik türünü ve özelliğin kısa bir açıklamasını gösterir. Özelliğin açıklamasını, kısayol menüsünde Açıklama komutunu kullanarak ve üzerinde açabilirsiniz.

> [!NOTE]
> Bu **Özellikler** penceresi araç çubuğu denetimi, tasarımcıda XAML dosyaları düzenlenirken kullanılamaz.

 Küçük resim görünümü tasarımcıda XAML dosyaları düzenlenirken seçili olan öğenin görsel temsilini gösterir.

 Arama, tasarımcıda XAML dosyalarını düzenlenirken Özellikler ve olaylar için bir arama işlevi sağlar. Arama kutusu, siz yazarken kısmi sözcük aramalarına ve güncelleştirmelerin arama sonuçlarına yanıt verir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Proje özellikleri başvuru](../../ide/reference/project-properties-reference.md) [pencere düzenlerini özelleştirme](../../ide/customizing-window-layouts-in-visual-studio.md)
