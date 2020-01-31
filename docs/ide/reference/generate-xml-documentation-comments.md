---
title: XML belgeleri yorumları Ekle
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 20381dd78f169e2b549e077992ac0d1dc1b5c44c
ms.sourcegitcommit: 6375001ab26786af8d4d449f5846f8a49779ed18
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2020
ms.locfileid: "76892148"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Nasıl yapılır: INSERT belgeleri oluşturmak için XML açıklamaları

Visual Studio size yardımcı olabilir belge sınıfları ve yöntemleri gibi kod öğeleri otomatik olarak standart XML belge açıklaması yapısını oluşturarak. Derleme zamanında içeren belge yorumlarını bir XML dosyası oluşturabilirsiniz.

> [!TIP]
> Oluşturulan XML dosyasının adını ve konumunu yapılandırma hakkında daha fazla bilgi için bkz. [XML açıklamaları ile Kodunuzu Belgeleme (C# kılavuz)](/dotnet/csharp/codedoc).

Visual Studio ve diğer Ide'leri IntelliSense türler ve üyeler hakkında hızlı bilgi göstermek için kullanabilirsiniz, böylece derleyici tarafından oluşturulan XML dosyasının yanı sıra .NET bütünleştirilmiş kodunuzda dağıtılabilir. Ayrıca, XML dosyasını gibi araçlarla çalıştırılabilir [DocFX](https://dotnet.github.io/docfx/) ve [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) API Başvurusu Web siteleri oluşturmak için.

> [!NOTE]
> **Açıklama Ekle** XML belgeleri yorumları otomatik olarak ekleyen komutu kullanılabilir [ C# ](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) ve [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation). Ancak, el ile ekleyebilirsiniz [c++ XML belgeleri yorumları](/cpp/build/reference/xml-documentation-visual-cpp) dosyaları ve yine de derleme zamanında XML belge dosyalarını oluştur.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Bir kod öğesi için XML açıklamaları eklemek için

1. Belge, örneğin, bir yöntem için istediğiniz öğeyi yukarıda metin imleci yerleştirin.

2. Aşağıdakilerden birini yapın:

   - Tür `///` içinde C#, veya `'''` Visual Basic'te

   - Gelen **Düzenle** menüsünde seçin **IntelliSense** > **Açıklama Ekle**

   - Seçin sağ tıklayın veya bağlam menüsünden veya yalnızca kod öğesi sonraki sürümlere **kod parçacığı** > **Açıklama Ekle**

   XML şablonu kod öğesi hemen oluşturulmaz. Örneğin, bir yöntem Yorum olduğunda ürettiği **\<Özet\>** öğesi, bir **\<param\>** her parametre ve bir öğesi **\<döndürür\>** dönüş değeri belge öğesi.

   ![XML açıklama şablonu-C#](media/doc-preview-cs.png)

   ![XML açıklama şablonu - Visual Basic](media/doc-preview-vb.png)

3. Her bir XML öğesinin kod öğesi tam olarak belge açıklamalarını girin.

   ![Tamamlanan açıklaması](media/doc-result-cs.png)

Öğe üzerine gelindiğinde hızlı bilgi içinde işlenecek XML açıklamalarındaki stilleri kullanabilirsiniz. Bu stiller şunlardır: italik, kalın, madde işaretleri ve tıklatılabilir bir bağlantı.

   ![Tamamlanan açıklaması](media/doc-styles-cs.png) 

> [!NOTE]
> Var olan bir [seçeneği](../../ide/reference/options-text-editor-csharp-advanced.md) yazdıktan sonra geçiş XML belge açıklamaları için `///` içinde C# veya `'''` Visual Basic. Menü çubuğundan seçin **Araçları** > **seçenekleri** açmak için **seçenekleri** iletişim kutusu. Ardından, gidin **metin düzenleyici**  >  **C#** veya **temel** > **Gelişmiş**. İçinde **Düzenleyici Yardımı** bölümünde, Aranan **XML belge açıklamaları oluştur** seçeneği.

## <a name="see-also"></a>Ayrıca bkz.

- [XML belgeleri yorumları (C# Programlama Kılavuzu)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [XML açıklamalarıyla kodunuzu belgeleme (C# Kılavuzu)](/dotnet/csharp/codedoc)
- [Nasıl yapılır: XML belgeleri (Visual Basic) oluşturma](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [C++ açıklamaları](/cpp/cpp/comments-cpp)
- [XML belgeleri (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Kod oluşturma](../code-generation-in-visual-studio.md)
