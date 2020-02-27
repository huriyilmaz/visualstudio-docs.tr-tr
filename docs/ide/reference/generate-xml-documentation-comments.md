---
title: XML belgeleri yorumları Ekle
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0e21d0617f954c0cc34975b7f8626b83966f6b5d
ms.sourcegitcommit: 9de7d25056da59df0941508c80c0b12766ba6580
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706406"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Nasıl yapılır: INSERT belgeleri oluşturmak için XML açıklamaları

Visual Studio size yardımcı olabilir belge sınıfları ve yöntemleri gibi kod öğeleri otomatik olarak standart XML belge açıklaması yapısını oluşturarak. Derleme zamanında içeren belge yorumlarını bir XML dosyası oluşturabilirsiniz.

> [!TIP]
> Oluşturulan XML dosyasının adını ve konumunu yapılandırma hakkında daha fazla bilgi için bkz. [XML açıklamaları ile Kodunuzu Belgeleme (C# kılavuz)](/dotnet/csharp/codedoc).

Visual Studio ve diğer Ide'leri IntelliSense türler ve üyeler hakkında hızlı bilgi göstermek için kullanabilirsiniz, böylece derleyici tarafından oluşturulan XML dosyasının yanı sıra .NET bütünleştirilmiş kodunuzda dağıtılabilir. Ayrıca, XML dosyası, API başvuru Web siteleri oluşturmak için [Docfx](https://dotnet.github.io/docfx/) ve [sandrole](https://www.microsoft.com/download/details.aspx?id=10526) gibi araçlar aracılığıyla çalıştırılabilir.

> [!NOTE]
> XML belgelerinin açıklamalarını otomatik olarak ekleyen **Yorum Ekle** komutu, [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) ve [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)kullanılabilir. Ancak, [XML belge açıklamalarını C++ ](/cpp/build/reference/xml-documentation-visual-cpp) dosyalara el ile ekleyebilir ve derleme zamanında XML belge dosyaları oluşturabilirsiniz.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Bir kod öğesi için XML açıklamaları eklemek için

1. Belge, örneğin, bir yöntem için istediğiniz öğeyi yukarıda metin imleci yerleştirin.

2. Aşağıdakilerden birini yapın:

   - `///` C#yazın veya `'''` Visual Basic

   - **Düzenle** menüsünde **IntelliSense** ' i seçin > **Açıklama Ekle**

   - Kod öğesinin üzerindeki veya hemen üstündeki sağ tıklama ya da bağlam menüsünden kod **parçacığı** > kod **Ekle** ' yi seçin.

   XML şablonu kod öğesi hemen oluşturulmaz. Örneğin, bir yöntemi yorumlama sırasında, her bir parametre için bir **\<param\>** öğesi **\<Özet\>** öğesi ve\<\>öğesi **döndürür** .

   ![XML açıklama şablonu-C#](media/doc-preview-cs.png)

   ![XML açıklama şablonu - Visual Basic](media/doc-preview-vb.png)

3. Her bir XML öğesinin kod öğesi tam olarak belge açıklamalarını girin.

   ![Tamamlanan açıklaması](media/doc-result-cs.png)

Öğe üzerine gelindiğinde hızlı bilgi içinde işlenecek XML açıklamalarındaki stilleri kullanabilirsiniz. Bu stiller şunlardır: italik, kalın, madde işaretleri ve tıklatılabilir bir bağlantı.

   ![Tamamlanan açıklaması](media/doc-style-cs.png) 

> [!NOTE]
> `///` C# veya `'''` Visual Basic YAZDıKTAN sonra XML belge açıklamalarını değiştirme [seçeneği](../../ide/reference/options-text-editor-csharp-advanced.md) vardır. **Seçenekler** iletişim kutusunu açmak için menü çubuğundan **Araçlar** > **Seçenekler** ' i seçin. Ardından, **metin düzenleyici** > **C#** veya **temel** > **Gelişmiş**' e gidin. **Düzenleyici yardım** bölümünde **XML belge açıklamaları oluştur** seçeneğini arayın.

## <a name="see-also"></a>Ayrıca bkz.

- [XML belge açıklamaları (C# Programlama Kılavuzu)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Kodunuzu XML açıklamalarıyla belgeleme (C# kılavuz)](/dotnet/csharp/codedoc)
- [Nasıl yapılır: XML belgeleri oluşturma (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [C++Açıklamaları](/cpp/cpp/comments-cpp)
- [XML belgeleri (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Kod oluşturma](../code-generation-in-visual-studio.md)
