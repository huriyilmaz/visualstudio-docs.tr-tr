---
title: XML belgesi açıklamalarını Ekle
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e9153677b833a89a236923a971b511548b064142
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668607"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Nasıl yapılır: belge oluşturmak için XML açıklamaları ekleme

Visual Studio, standart XML belgesi Açıklama yapısını otomatik olarak oluşturarak sınıflar ve yöntemler gibi kod öğelerini belgeetmenize yardımcı olabilir. Derleme zamanında belge açıklamalarını içeren bir XML dosyası oluşturabilirsiniz.

> [!TIP]
> Oluşturulan XML dosyasının adını ve konumunu yapılandırma hakkında daha fazla bilgi için bkz. [XML açıklamaları ile Kodunuzu Belgeleme (C# kılavuz)](/dotnet/csharp/codedoc).

Derleyici tarafından oluşturulan XML dosyası, Visual Studio ve diğer IDE 'Ler, türler ve Üyeler hakkında hızlı bilgi göstermek için IntelliSense kullanabilmesi için .NET derlemenizin yanı sıra dağıtılabilir. Ayrıca, XML dosyası, API başvuru Web siteleri oluşturmak için [Docfx](https://dotnet.github.io/docfx/) ve [sandrole](https://www.microsoft.com/download/details.aspx?id=10526) gibi araçlar aracılığıyla çalıştırılabilir.

> [!NOTE]
> XML belgelerinin açıklamalarını otomatik olarak ekleyen **Yorum Ekle** komutu, [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) ve [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)kullanılabilir. Ancak, [XML belge açıklamalarını C++ ](/cpp/build/reference/xml-documentation-visual-cpp) dosyalara el ile ekleyebilir ve derleme zamanında XML belge dosyaları oluşturabilirsiniz.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Bir kod öğesi için XML açıklamaları eklemek için

1. Metin imlecinizi, belge, örneğin bir yöntem gibi, belgelemek istediğiniz öğenin üzerine yerleştirin.

1. Aşağıdakilerden birini yapın:

   - @No__t_0 C#yazın veya `'''` Visual Basic

   - **Düzenle** menüsünde **IntelliSense** ' i seçin  > **Açıklama Ekle**

   - Kod öğesinin üzerindeki veya hemen üstündeki sağ tıklama ya da bağlam menüsünden kod **parçacığı**  >  kod**Ekle** ' yi seçin.

   XML şablonu, hemen kod öğesinin üzerinde oluşturulur. Örneğin, bir yöntemi yorumlama sırasında, **\<summary \>** öğesi, her parametre için bir **\<param \>** öğesi ve döndürülen değeri belgelemek için bir **\<returns \>** öğesi oluşturur.

   ![XML açıklama şablonu-C#](media/doc-preview-cs.png)

   ![XML açıklama şablonu-Visual Basic](media/doc-preview-vb.png)

1. Kod öğesini tam olarak belgelemek için her bir XML öğesinin açıklamalarını girin.

   ![Açıklama tamamlandı](media/doc-result-cs.png)

> [!NOTE]
> @No__t_1 C# veya `'''` Visual Basic YAZDıKTAN sonra XML belge açıklamalarını değiştirme [seçeneği](../../ide/reference/options-text-editor-csharp-advanced.md) vardır. **Seçenekler** iletişim kutusunu açmak için menü çubuğundan **Araçlar**  > **Seçenekler** ' i seçin. Ardından, **metin düzenleyici**  > **C#** veya **temel**  > **Gelişmiş**' e gidin. **Düzenleyici yardım** bölümünde **XML belge açıklamaları oluştur** seçeneğini arayın.

## <a name="see-also"></a>Ayrıca bkz.

- [XML belge açıklamaları (C# Programlama Kılavuzu)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Kodunuzu XML açıklamalarıyla belgeleme (C# kılavuz)](/dotnet/csharp/codedoc)
- [Nasıl yapılır: XML belgeleri oluşturma (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [C++Açıklamaları](/cpp/cpp/comments-cpp)
- [XML belgeleri (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Kod oluşturma](../code-generation-in-visual-studio.md)