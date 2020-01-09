---
title: Model Gezginini Özelleştirme
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96c12ac2063e6b3ac04e3c0e9b0c20c69ea91a35
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589714"
---
# <a name="customizing-the-model-explorer"></a>Model Gezginini Özelleştirme
Etki alanına özgü dil tasarlayana ait Gezgin görünümünü ve davranışını aşağıdaki şekilde değiştirebilirsiniz:

- Pencere başlığını değiştirin.

- Sekme simgesini değiştirin.

- Düğümlerin simgelerini değiştirin.

- Düğümleri gizleyin.

## <a name="changing-the-window-title"></a>Pencere başlığını değiştirme
 Oluşturulan gezgin 'in pencere başlığını değiştirmek için, **DSL Gezgini**'Nde **Gezgin davranışı** ' nı seçin ve ardından **Özellikler** penceresinde **başlık** özelliğini istediğiniz başlığa ayarlayın.

## <a name="changing-the-tab-icon"></a>Sekme simgesini değiştirme
 Gezgin 'in sekme simgesini değiştirmek için. BMP dosyasında 16x16 piksellik bir simge kullanın. Simge dosyasını \DslPackage\Resources\ klasörüne yerleştirin ve ardından dosya adını **Modelexplorertoolwindowbitmap. bmp**olarak değiştirin. Örneğin, Visual Studio Setup. ico simge dosyasını. bmp biçiminde değiştirebilir ve **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**olarak yeniden adlandırabilirsiniz. Oluşturulan tasarımcı, **Çözüm Gezgini**birlikte yuvalandığında, bu simgeyi gezgin 'in sekmesinde görüntüler.

## <a name="setting-custom-icons-on-explorer-nodes"></a>Gezgin düğümlerinde özel simgeler ayarlama
 Gezgin düğüm ayarlarını kullanarak, gezginizdeki düğümleri özelleştirebilirsiniz. Aşağıdaki yordam, bir düğüme bir simgenin nasıl ekleneceğini gösterir.

#### <a name="to-add-an-icon-to-an-explorer-node"></a>Gezgin düğümüne simge eklemek için

1. Görev akışı çözüm şablonunu kullanarak bir [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] çözümü oluşturun.

2. Çözümdeki **Dsl\resources** klasörüne 16x16 piksellik bir simge içeren bir. bmp dosyası yerleştirin.

3. **DSL Gezgini**' nde **Gezgin davranışı** ' na sağ tıklayın ve ardından **Yeni Gezgin düğüm ayarları ekle**' ye tıklayın.

    **Özel düğüm ayarları** düğümünün altında bir **ExplorerNodeSettings** düğümü görüntülenir.

4. **ExplorerNodeSettings**' i seçin ve ardından **Özellikler** penceresinde **sınıfı** **aktör**olarak ayarlayın.

5. Simge dosyasının yolunu **gösterecek şekilde** ayarlayın.

6. Tüm şablonları dönüştürün ve Çözümü derleyin ve çalıştırın.

7. Oluşturulan tasarımcıda örnek diyagramı açın.

    Gezgin, simgenizi içeren üç **aktör** düğümü göstermelidir.

> [!NOTE]
> Oluşturulan Gezgin içinde görüntülenen herhangi bir öğe için bir düğüm simgesi ayarladıysanız, tüm gezgin düğümleri simgeyi görüntüler. Hiçbir simge ayarlanmamışsa, düğümler varsayılan simgeyi görüntüler.

## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Gezgin düğümünde görünen adı değiştirme
 Bir model öğeleri adının Gezgini 'nde görüntülenme şeklini değiştirebilirsiniz. Aşağıdaki yordam, yorum düğümündeki bir **yorum** tarafından başvurulan **görevin** adının nasıl görüntüleneceğini gösterir.

#### <a name="to-display-a-property"></a>Bir özelliği görüntüleme

1. Önceki yordamda oluşturduğunuz çözümü açın.

2. Bir rolün çoğulluk özelliğini 0.. **1 olarak ayarlayarak** , **açıklamanın** yalnızca tek bir etki alanı sınıfına başvurduğundan emin olun. Özellik adının **konusu**olması gerekir ve ilişki adı, **CommentReferencesSubject**olmalıdır.

3. **DSL Gezgini**' nde **Gezgin davranışı** ' na sağ tıklayın ve ardından **Yeni Gezgin düğüm ayarları ekle**' ye tıklayın.

     **Özel düğüm ayarları** düğümünün altında bir **ExplorerNodeSettings** düğümü görüntülenir.

4. **ExplorerNodeSettings**' i seçin ve ardından **Özellikler** penceresinde **sınıfı** **Açıklama**olarak ayarlayın.

5. **Yorum** düğümüne sağ tıklayın ve ardından **yeni özellik yolu Ekle**' ye tıklayın.

     **Görüntülenen özellik**adlı yeni bir düğüm görüntülenir.

6. **Görüntülenecek özellik**' i seçin ve ardından **Özellikler** penceresinde, **özelliğin yolunu**olan değer alanına tıklayın. **Açıklama**' yı ve ardından **CommentReferencesSubject**' **i seçin.** Elde edilen yol, **CommentReferencesSubject. Subject/! ' a benzemelidir. Konu**.

7. **Özelliğin**değer alanında **ad**' ı seçin.

8. Tüm şablonları dönüştürün ve çözümünüzü derleyin ve çalıştırın.

9. Oluşturulan tasarımcıda örnek diyagramı açın.

10. Diyagramda Comment öğesi ve **Task1** öğesi arasında bir **Açıklama Bağlayıcısı** çizin.

     Gezgin düğümü, yorumu **Task1**olarak görüntülemelidir.

## <a name="hiding-nodes"></a>Düğümleri gizleme
 Kendi yolunu **DSL Gezgini**'Nin **Gizli düğümler** düğümüne ekleyerek, gezginizdeki bir düğümü gizleyebilirsiniz. Aşağıdaki yordamda, **Açıklama** düğümlerinin nasıl gizlenmesi gösterilmektedir.

#### <a name="to-hide-an-explorer-node"></a>Gezgin düğümünü gizlemek için

1. Önceki yordamda oluşturduğunuz çözümü açın.

2. **DSL Gezgini**' nde **Gezgin davranışı** ' na sağ tıklayın ve ardından **yeni etki alanı yolu Ekle**' ye tıklayın.

     **Gizli düğümler**altında bir **etki alanı yolu** düğümü görüntülenir.

3. **Etki alanı yolu**' nu seçin ve ardından **Özellikler** penceresinde **yol tanımının**değer alanına tıklayın. **FlowGraph**ve **FlowGraphHasComments**öğelerini seçin. Elde edilen yol **FlowGraphHasComments. Comments** öğesine benzemelidir

4. Tüm şablonları dönüştürün ve çözümünüzü derleyin ve çalıştırın.

5. Oluşturulan tasarımcıda örnek diyagramı açın.

     Gezgin yalnızca bir **aktör** düğümü göstermelidir ve **açıklamalar** düğümünü göstermemelidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Etki alanına özgü dil araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
