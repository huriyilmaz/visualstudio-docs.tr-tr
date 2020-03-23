---
title: XML dokümantasyon açıklamaları ekleme
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0e21d0617f954c0cc34975b7f8626b83966f6b5d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77706406"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Nasıl yapılsın: Belge oluşturma için XML açıklamaları ekleme

Visual Studio, standart XML dokümantasyon yorum yapısını otomatik olarak oluşturarak sınıflar ve yöntemler gibi kod öğelerini belgelemenize yardımcı olabilir. Derleme zamanında, belge açıklamalarını içeren bir XML dosyası oluşturabilirsiniz.

> [!TIP]
> Oluşturulan XML dosyasının adını ve konumunu yapılandırma hakkında bilgi için [kodunuzu XML yorumlarıyla belgeleme (C# Guide)](/dotnet/csharp/codedoc)bölümüne bakın.

Derleyici tarafından oluşturulan XML dosyası .NET derlemenizin yanında dağıtılabilir, böylece Visual Studio ve diğer IDA'lar türleri ve üyeleri hakkında hızlı bilgi göstermek için IntelliSense'i kullanabilir. Ayrıca, XML dosyası API başvuru web siteleri oluşturmak için [DocFX](https://dotnet.github.io/docfx/) ve [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) gibi araçlar aracılığıyla çalıştırılabilir.

> [!NOTE]
> XML dokümantasyon yorumlarını otomatik olarak ekleyen **Açıklama Ekle** komutu [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) ve [Visual Basic'te](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)kullanılabilir. Ancak, C++ dosyalarına [XML dokümantasyon yorumlarını](/cpp/build/reference/xml-documentation-visual-cpp) el ile ekleyebilir ve derleme zamanında XML dokümantasyon dosyaları oluşturmaya devam edebilirsiniz.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Kod öğesi için XML açıklamaları eklemek için

1. Metin imlecinizi belgelemek istediğiniz öğenin (örneğin bir yöntem) üzerine yerleştirin.

2. Aşağıdakilerden birini yapın:

   - `///` C#veya Visual `'''` Basic yazın

   - **Edit** menüsünden **IntelliSense** > **Insert Comment'u** seçin

   - Kod öğesinin sağ tıklama veya bağlam menüsünden veya hemen üstündeki **Snippet** > **Insert Comment'u** seçin

   XML şablonu hemen kod öğesinin üzerinde oluşturulur. Örneğin, bir yöntem yorumlarken, ** \<özet\> ** öğe, her parametre için bir ** \<param\> ** öğesi ve döndürme değerini belgelemek için bir ** \<iade\> ** öğesi oluşturur.

   ![XML yorum şablonu - C #](media/doc-preview-cs.png)

   ![XML yorum şablonu - Visual Basic](media/doc-preview-vb.png)

3. Kod öğesini tam olarak belgelemek için her XML öğesi için açıklamalar girin.

   ![Tamamlanan açıklama](media/doc-result-cs.png)

XML yorumlarında, öğenin üzerinde gezinirken Hızlı Bilgi'de işleyecek stilleri kullanabilirsiniz. Bu stilleri şunlardır: italics, kalın, madde işaretleri ve tıklanabilir bir bağlantı.

   ![Tamamlanan açıklama](media/doc-style-cs.png) 

> [!NOTE]
> C# [option](../../ide/reference/options-text-editor-csharp-advanced.md) veya `'''` Visual Basic'i yazdıktan `///` sonra XML dokümantasyon yorumlarını geçiş seçeneği vardır. Menü çubuğundan **Seçenekler** iletişim kutusunu açmak için **Araçlar** > **Seçenekleri'ni** seçin. Ardından, **Text Editor** > **C#** veya **Basic** > **Advanced'e**gidin. Düzenleyici **Yardımı** bölümünde, **XML belge oluşturma yorumlarını oluştur** seçeneğini arayın.

## <a name="see-also"></a>Ayrıca bkz.

- [XML dokümantasyon yorumları (C# Programlama Kılavuzu)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Kodunuzu XML yorumlarıyla belgeleme (C# Kılavuzu)](/dotnet/csharp/codedoc)
- [Nasıl yapılır: XML belgeleri oluşturma (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [C++ Yorumları](/cpp/cpp/comments-cpp)
- [XML Dokümantasyon (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Kod oluşturma](../code-generation-in-visual-studio.md)
