---
title: XML belge açıklamalarını ekleme
description: .NET derlemenize ek olarak dağıtmak üzere derleyici tarafından oluşturulan bir XML dosyası oluşturmak için kullanabileceğiniz XML belge açıklamalarını kodunuza ekleme hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: a0319b511ddc55e0a6aa0297c924fbfbe14c6c34
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726874"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Nasıl yapılır: Belge oluşturma için XML yorumları ekleme

Visual Studio, standart XML belge açıklaması yapısını otomatik olarak oluşturarak sınıflar ve yöntemler gibi kod öğelerini belgelemeniz için size yardımcı olabilir. Derleme zamanında, belge açıklamalarını içeren bir XML dosyası oluşturabilirsiniz.

> [!TIP]
> Oluşturulan XML dosyasının adını ve konumunu yapılandırma hakkında bilgi için bkz. Kodunuzu XML açıklamalarını kullanarak belgele [(C# Kılavuzu)](/dotnet/csharp/codedoc).

Derleyici tarafından oluşturulan XML dosyası. .NET derlemeniz ile birlikte dağıtıldığından, Visual Studio ve diğer IDE'ler türler ve üyeler hakkında hızlı bilgiler göstermek için IntelliSense kullanabilir. Buna ek olarak XML dosyası, API başvuru web siteleri oluşturmak için [DocFX](https://dotnet.github.io/docfx/) ve [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) gibi araçlar aracılığıyla çalıştırabilirsiniz.

> [!NOTE]
> XML **belge açıklamalarını** otomatik olarak ekseren Açıklama Ekle komutu [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) ile kullanılabilir ve [Visual Basic.](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation) Ancak, C++ dosyalarına [XML belge açıklamalarını el ile ekleyebilirsiniz](/cpp/build/reference/xml-documentation-visual-cpp) ve yine de derleme zamanında XML belge dosyaları oluşturabilirsiniz.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Bir kod öğesine XML yorumları eklemek için

1. Metin imlecinizi, belgeye almak istediğiniz öğenin (örneğin, bir yöntemi) üzerine ekleyin.

2. Aşağıdakilerden birini yapın:

   - `///`C# veya Visual Basic `'''`

   - Düzenle menüsünde **IntelliSense Açıklama Ekle'yi**   >  **seçin**

   - Kod öğesinin sağ tıklama veya bağlam menüsünden Kod Parçacığı Ekleme  >  **Açıklaması'yı seçin**

   XML şablonu hemen kod öğesinin üzerinde oluşturulur. Örneğin, bir yönteme açıklama eklerken öğe, her parametre için bir öğe ve dönüş değerini **\<summary\>** **\<param\>** **\<returns\>** belgeleye bir öğesi üretir.

   ![XML açıklama şablonu - C #](media/doc-preview-cs.png)

   ![XML açıklama şablonu - Visual Basic](media/doc-preview-vb.png)

3. Kod öğesini tam olarak belgeley etmek için her XML öğesinin açıklamalarını girin.

   ![Tamamlanan açıklamayı gösteren ekran görüntüsü.](media/doc-result-cs.png)

Öğesinin üzerine gelindiğinde Hızlı Bilgi'de işılacak XML açıklamalarında stilleri kullanabilirsiniz. Bu stiller şunları içerir: italik, kalın, madde işaretleri ve tıklanabilir bir bağlantı.

   ![İtalik, kalın, madde işaretleri ve tıklanabilir bağlantı için stil etiketlerini içeren tamamlanmış açıklamayı gösteren ekran görüntüsü.](media/doc-style-cs.png) 

> [!NOTE]
> C# [veya daha](../../ide/reference/options-text-editor-csharp-advanced.md) sonra XML belge açıklamalarını açıp `///` `'''` Visual Basic. Seçenekler iletişim kutusunu açmak için **menü**  >  **çubuğundan** Araçlar **Seçenekler'i** seçin. Ardından Metin Düzenleyici  >  **C#** veya Temel **Gelişmiş'e**  >  **gidin.** Düzenleyici **Yardımı bölümünde** XML belge **açıklamalarını oluştur seçeneğini** belirleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [XML belgeleri yorumları (C# Programlama Kılavuzu)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [XML açıklamalarını kullanarak kodunuzu belgele (C# Kılavuzu)](/dotnet/csharp/codedoc)
- [Nasıl: XML belgeleri oluşturma (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [C++ Yorumları](/cpp/cpp/comments-cpp)
- [XML Belgeleri (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Kod oluşturma](../code-generation-in-visual-studio.md)
