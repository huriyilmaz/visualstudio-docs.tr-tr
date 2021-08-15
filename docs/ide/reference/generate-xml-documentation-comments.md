---
title: XML belgesi açıklamalarını Ekle
description: Kodunuzda, .NET derlemenizin yanı sıra dağıtmak üzere derleyicinin ürettiği bir XML dosyası oluşturmak için kullanabileceğiniz XML belge açıklamalarını ekleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 5b538fe8b9f9ab61486f49efb33fac56356ae1c2ffdd9051e39687696c392b62
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121357420"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Nasıl yapılır: belge oluşturmak için XML açıklamaları ekleme

Visual Studio, standart XML belgesi açıklama yapısını otomatik olarak oluşturarak sınıflar ve yöntemler gibi kod öğelerini belgeetmenize yardımcı olabilir. Derleme zamanında belge açıklamalarını içeren bir XML dosyası oluşturabilirsiniz.

> [!TIP]
> Oluşturulan XML dosyasının adını ve konumunu yapılandırma hakkında daha fazla bilgi için bkz. [kodunuzu XML yorumlarıyla belgeleme (C# Kılavuzu)](/dotnet/csharp/codedoc).

derleyici tarafından oluşturulan XML dosyası, Visual Studio ve diğer ıdes 'ler, türler ve üyeler hakkında hızlı bilgileri göstermek için ıntellisense kullanabilmesi için .net derlemenizin yanı sıra dağıtılabilir. Ayrıca, XML dosyası, API başvuru Web siteleri oluşturmak için [Docfx](https://dotnet.github.io/docfx/) ve [sandrole](https://www.microsoft.com/download/details.aspx?id=10526) gibi araçlar aracılığıyla çalıştırılabilir.

> [!NOTE]
> XML belgelerinin açıklamalarını otomatik olarak ekleyen **Yorum Ekle** komutu [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) ve [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)kullanılabilir. Ancak, [C++ dosyalarına XML belge açıklamalarını](/cpp/build/reference/xml-documentation-visual-cpp) el ile ekleyebilir ve derleme zamanında XML belge dosyaları oluşturabilirsiniz.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Bir kod öğesi için XML açıklamaları eklemek için

1. Metin imlecinizi, belge, örneğin bir yöntem gibi, belgelemek istediğiniz öğenin üzerine yerleştirin.

2. Aşağıdakilerden birini yapın:

   - `///`C# yazın veya `'''` Visual Basic

   - **Düzenle** menüsünde **IntelliSense**  >  **Açıklama Ekle** ' yi seçin.

   - Code öğesinin üzerindeki veya hemen üstündeki sağ tıklama ya da bağlam menüsünde kod **parçacığı**  >  **Ekle açıklama** ' yı seçin.

   XML şablonu, hemen kod öğesinin üzerinde oluşturulur. Örneğin, bir yöntemi yorumlama sırasında, **\<summary\>** öğe, **\<param\>** her parametre için bir öğe ve **\<returns\>** dönüş değerini belgelemek için bir öğe oluşturur.

   ![XML açıklama şablonu-C #](media/doc-preview-cs.png)

   ![XML açıklama şablonu-Visual Basic](media/doc-preview-vb.png)

3. Kod öğesini tam olarak belgelemek için her bir XML öğesinin açıklamalarını girin.

   ![Tamamlanan yorumu gösteren ekran görüntüsü.](media/doc-result-cs.png)

Öğe üzerine gelindiğinde hızlı bilgi içinde işlenecek XML açıklamalarındaki stilleri kullanabilirsiniz. Bu stiller şunlardır: italik, kalın, madde işaretleri ve tıklatılabilir bir bağlantı.

   ![İtalik, kalın, madde işaretleri ve tıklatılabilir bir bağlantı için stil etiketleriyle tamamlanan açıklamayı gösteren ekran görüntüsü.](media/doc-style-cs.png) 

> [!NOTE]
> C# veya Visual Basic yazdıktan sonra XML belge açıklamalarını değiştirme [seçeneği](../../ide/reference/options-text-editor-csharp-advanced.md) vardır `///` `'''` . Menü çubuğundan **Araçlar**  >  **Seçenekler** ' i seçerek **Seçenekler** iletişim kutusunu açın. Sonra, **metin düzenleyici**  >  **C#** veya **temel**  >  **Gelişmiş**' e gidin. **Düzenleyici yardım** bölümünde **XML belge açıklamaları oluştur** seçeneğini arayın.

## <a name="see-also"></a>Ayrıca bkz.

- [XML belgeleri Yorumları (C# Programlama Kılavuzu)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Kodunuzu XML açıklamalarıyla belgeleme (C# Kılavuzu)](/dotnet/csharp/codedoc)
- [Nasıl yapılır: XML belgeleri oluşturma (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [C++ açıklamaları](/cpp/cpp/comments-cpp)
- [XML belgeleri (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Kod oluşturma](../code-generation-in-visual-studio.md)
