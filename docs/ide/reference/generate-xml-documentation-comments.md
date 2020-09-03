---
title: XML belgesi açıklamalarını Ekle
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0e21d0617f954c0cc34975b7f8626b83966f6b5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77706406"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Nasıl yapılır: belge oluşturmak için XML açıklamaları ekleme

Visual Studio, standart XML belgesi Açıklama yapısını otomatik olarak oluşturarak sınıflar ve yöntemler gibi kod öğelerini belgeetmenize yardımcı olabilir. Derleme zamanında belge açıklamalarını içeren bir XML dosyası oluşturabilirsiniz.

> [!TIP]
> Oluşturulan XML dosyasının adını ve konumunu yapılandırma hakkında daha fazla bilgi için bkz. [kodunuzu XML yorumlarıyla belgeleme (C# Kılavuzu)](/dotnet/csharp/codedoc).

Derleyici tarafından oluşturulan XML dosyası, Visual Studio ve diğer IDE 'Ler, türler ve Üyeler hakkında hızlı bilgi göstermek için IntelliSense kullanabilmesi için .NET derlemenizin yanı sıra dağıtılabilir. Ayrıca, XML dosyası, API başvuru Web siteleri oluşturmak için [Docfx](https://dotnet.github.io/docfx/) ve [sandrole](https://www.microsoft.com/download/details.aspx?id=10526) gibi araçlar aracılığıyla çalıştırılabilir.

> [!NOTE]
> XML belgelerinin açıklamalarını otomatik olarak ekleyen **Yorum Ekle** komutu [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) ve [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)kullanılabilir. Ancak, [C++ dosyalarına XML belge açıklamalarını](/cpp/build/reference/xml-documentation-visual-cpp) el ile ekleyebilir ve derleme zamanında XML belge dosyaları oluşturabilirsiniz.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Bir kod öğesi için XML açıklamaları eklemek için

1. Metin imlecinizi, belge, örneğin bir yöntem gibi, belgelemek istediğiniz öğenin üzerine yerleştirin.

2. Şunlardan birini yapın:

   - `///`C# yazın veya `'''` Visual Basic

   - **Düzenle** menüsünde **IntelliSense**  >  **Açıklama Ekle** ' yi seçin.

   - Code öğesinin üzerindeki veya hemen üstündeki sağ tıklama ya da bağlam menüsünde kod **parçacığı**  >  **Ekle açıklama** ' yı seçin.

   XML şablonu, hemen kod öğesinin üzerinde oluşturulur. Örneğin, bir yöntemi yorumlama sırasında, **\<summary\>** öğe, **\<param\>** her parametre için bir öğe ve **\<returns\>** dönüş değerini belgelemek için bir öğe oluşturur.

   ![XML açıklama şablonu-C #](media/doc-preview-cs.png)

   ![XML açıklama şablonu-Visual Basic](media/doc-preview-vb.png)

3. Kod öğesini tam olarak belgelemek için her bir XML öğesinin açıklamalarını girin.

   ![Açıklama tamamlandı](media/doc-result-cs.png)

Öğe üzerine gelindiğinde hızlı bilgi içinde işlenecek XML açıklamalarındaki stilleri kullanabilirsiniz. Bu stiller şunlardır: italik, kalın, madde işaretleri ve tıklatılabilir bir bağlantı.

   ![Açıklama tamamlandı](media/doc-style-cs.png) 

> [!NOTE]
> C# veya Visual Basic yazdıktan sonra XML belge açıklamalarını değiştirme [seçeneği](../../ide/reference/options-text-editor-csharp-advanced.md) vardır `///` `'''` . Menü çubuğundan **Araçlar**  >  **Seçenekler** ' i seçerek **Seçenekler** iletişim kutusunu açın. Sonra, **metin düzenleyici**  >  **C#** veya **temel**  >  **Gelişmiş**' e gidin. **Düzenleyici yardım** bölümünde **XML belge açıklamaları oluştur** seçeneğini arayın.

## <a name="see-also"></a>Ayrıca bkz.

- [XML belgeleri Yorumları (C# Programlama Kılavuzu)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Kodunuzu XML açıklamalarıyla belgeleme (C# Kılavuzu)](/dotnet/csharp/codedoc)
- [Nasıl yapılır: XML belgeleri oluşturma (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [C++ açıklamaları](/cpp/cpp/comments-cpp)
- [XML belgeleri (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Kod oluşturma](../code-generation-in-visual-studio.md)
