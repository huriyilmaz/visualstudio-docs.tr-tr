---
title: 'İzlenecek yol: Kod parçacığı oluşturma'
description: 'Üç adımda kod parçacığı oluşturmayı öğrenin: bir XML dosyası oluşturun, uygun öğeleri girin ve kodunuzu buna ekleyin.'
ms.custom: SEO-VS-2020
ms.date: 03/31/2020
ms.topic: how-to
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 39565b95b93e489a739c2da3a0f88fb9f683a2bc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873807"
---
# <a name="walkthrough-create-a-code-snippet"></a>İzlenecek yol: Kod parçacığı oluşturma

Yalnızca birkaç adımdan oluşan bir kod parçacığı oluşturabilirsiniz. Yapmanız gereken tek şey bir XML dosyası oluşturur, uygun öğeleri doldurur ve kodunuzu buna ekler. İsteğe bağlı olarak değiştirme parametrelerini ve proje başvurularını kullanabilirsiniz. **Kod parçacıkları yöneticisinin** (**Araçlar**   >  **kod parçacıkları Yöneticisi**) içeri aktar düğmesini kullanarak kod parçacığını Visual Studio yüklemenize aktarın.

## <a name="snippet-template"></a>Kod parçacığı şablonu

Aşağıdaki XML, temel kod parçacığı şablonudur:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title></Title>
        </Header>
        <Snippet>
            <Code Language="">
                <![CDATA[]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="create-a-code-snippet"></a>Kod parçacığı oluşturma

1. Visual Studio 'da yeni bir XML dosyası oluşturun ve yukarıda gösterilen şablonu ekleyin.

2. **Başlık** öğesindeki kod parçacığının başlığını girin. Başlık **karekökünü** kullanın.

3. **Kod** öğesinin **Language** özniteliğinde parçacığın dilini girin. C# için **CSharp** kullanın, Visual Basic, **vb** kullanın ve C++ için **cpp** kullanın.

   > [!TIP]
   > Kullanılabilir tüm dil değerlerini görmek için [kod parçacıkları şema başvurusu](code-snippets-schema-reference.md) sayfasındaki [kod öğesi öznitelikleri bölümüne](code-snippets-schema-reference.md#attributes) gidin.

4. **Kod** öğesinin içindeki **CDATA** bölümüne kod parçacığı kodunu ekleyin.

   C# için:

   ```xml
   <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt(16);]]>
   </Code>
   ```

   Veya Visual Basic için:

   ```xml
   <Code Language="VB">
       <![CDATA[Dim root = Math.Sqrt(16)]]>
   </Code>
   ```

   > [!NOTE]
   > Kod parçacığının **CDATA** bölümündeki kod satırlarının nasıl girintileneceği veya biçimlendirilmesi gerektiğini belirtemezsiniz. Ekleme sırasında, dil hizmeti eklenen kodu otomatik olarak biçimlendirir.

5. Kod parçacığını *SquareRoot. parçacığını* (istediğiniz yere kaydedebilirsiniz) olarak kaydedin.

## <a name="import-a-code-snippet"></a>Kod parçacığını içeri aktarma

1. **Kod parçacıkları Yöneticisi 'ni** kullanarak Visual Studio yüklemenize bir kod parçacığı aktarabilirsiniz. **Araçlar**  >  **kod parçacıkları Yöneticisi**' ni seçerek açın.

2. **Al** düğmesine tıklayın.

3. Kod parçacığını önceki yordamda kaydettiğiniz konuma gidin, seçin ve **Aç**' a tıklayın.

4. **Kod parçacığını Içeri aktar** iletişim kutusu açılarak sağ bölmedeki seçimlerden parçacığın nereye ekleneceğini seçmenizi ister. Seçimlerinizden biri **kod** parçacıklarında olmalıdır. Seçin ve **son**' a ve ardından **Tamam**' a tıklayın.

5. Kod diline bağlı olarak, kod parçacığı aşağıdaki konumlardan birine kopyalanır:

   ::: moniker range="vs-2017"

   *%Userprofile%\Snippets\Visual Studio 2017 \ Code C# \Code parçacıkları*  
   *%Userprofile%\, Studio 2017 \ Code Snippets\Visual Basic\code parçacıkları*

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   *%Userprofile%\, Studio 2019 \ Code Snippets\Visual C# \Code parçacıkları*  
   *%Userprofile%\, Studio 2019 \ Code Snippets\Visual Basic\code parçacıkları*

   ::: moniker-end

6. Bir C# veya Visual Basic projesi açarak kod parçacığınızı test edin. Düzenleyicide bir kod dosyası açıkken,   >  sağ tıklama menüsünde kod **parçacığı Ekle** ' yi ve ardından **kod parçacılarımı** seçin. **Kare kök** adlı bir kod parçacığı görmeniz gerekir. Çift tıklayın.

   Kod parçacığı kodu kod dosyasına eklenir.

## <a name="description-and-shortcut-fields"></a>Açıklama ve kısayol alanları

::: moniker range="vs-2017"

1. Açıklama alanları, kod parçacıkları yöneticisinde görüntülenirken kod parçacığınızı hakkında daha fazla bilgi verir. Kısayol, kod parçacığınızı eklemek için kullanıcıların yazsaykullandığı bir etikettir. *%Userprofile%\, Studio 2017 \ kod parçacıkları \\ [Visual C# veya Visual Basic] \Code Snippet\SquareRoot.snippet* dosyasını açarak eklemiş olduğunuz kod parçacığını düzenleyin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Açıklama alanları, kod parçacıkları yöneticisinde görüntülenirken kod parçacığınızı hakkında daha fazla bilgi verir. Kısayol, kod parçacığınızı eklemek için kullanıcıların yazsaykullandığı bir etikettir. *%Userprofile%\, Studio 2019 \ kod parçacıkları \\ [Visual C# veya Visual Basic] \Code Snippet\SquareRoot.snippet* dosyasını açarak eklemiş olduğunuz kod parçacığını düzenleyin.

::: moniker-end

   > [!TIP]
   > Dosyayı Visual Studio 'Nun yerleştirdiği dizinde düzenlemekte olduğunuzdan, Visual Studio 'ya yeniden içeri aktarmanız gerekmez.

2. **Üstbilgi** öğesine **Yazar** ve **Açıklama** öğeleri ekleyin ve bunları içine girin.

3. **Header** öğesi şuna benzer görünmelidir:

   ```xml
   <Header>
       <Title>Square Root</Title>
       <Author>Myself</Author>
       <Description>Calculates the square root of 16.</Description>
   </Header>
   ```

4. **Kod parçacıkları yöneticisini** açın ve kod parçacığını seçin. Sağ bölmede, **Açıklama** ve **Yazar** alanlarının artık doldurulduğuna dikkat edin.

   ![Kod parçacığı Yöneticisi 'nde kod parçacığı açıklaması](media/code-snippet-description-author.png)

5. Bir kısayol eklemek için, **üst bilgi** öğesinin Içine bir **kısayol** öğesi ekleyin:

   ```xml
   <Header>
      <Title>Square Root</Title>
      <Author>Myself</Author>
      <Description>Calculates the square root of 16.</Description>
      <Shortcut>sqrt</Shortcut>
    </Header>
   ```

6. Kod parçacığı dosyasını yeniden kaydedin.

7. Kısayolu test etmek için, daha önce kullandığınız projeyi açın, düzenleyiciye **sqrt** yazın ve **Tab** tuşuna basın (Visual Basic için bir kez C# için iki kez).

   Kod parçacığı kodu eklenir.

## <a name="replacement-parameters"></a>Değiştirme parametreleri

Kod parçacığının bölümlerinin Kullanıcı tarafından değiştirilmesini isteyebilirsiniz. Örneğin, kullanıcının bir değişken adını geçerli projesindeki bir adla değiştirmesini isteyebilirsiniz. İki tür değiştirme sağlayabilirsiniz: değişmez değerler ve nesneler. Kod parçacığı içinde tamamen yer alan, ancak koda eklendikten sonra özelleştirilme olasılığı olan bir kod parçasının yerini belirlemek için [değişmez öğe öğesini](code-snippets-schema-reference.md#literal-element) kullanın (örneğin, bir dize veya sayısal değer). Kod parçacığı için gerekli olan, ancak bir nesne örneği veya bir denetim gibi tanımlanabilmesi muhtemel olan bir öğeyi tanımlamak için [Object öğesini](code-snippets-schema-reference.md#object-element) kullanın.

1. Kullanıcının kare kökünü hesaplamak üzere sayıyı kolayca değiştirmesini sağlamak için, *SquareRoot. parçacığının* dosyasının **kod parçacığı** öğesini aşağıdaki gibi değiştirin:

   ```xml
   <Snippet>
     <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt($Number$);]]>
     </Code>
     <Declarations>
       <Literal>
         <ID>Number</ID>
         <ToolTip>Choose the number you want the square root of.</ToolTip>
         <Default>16</Default>
       </Literal>
     </Declarations>
   </Snippet>
   ```

   Değişmez değer yerine bir ID () verildiğine dikkat edin `Number` . Bu KIMLIĞE, kod parçacığının içinden karakterlerle çevreleyerek başvurulur `$` :

   ```xml
   <![CDATA[double root = Math.Sqrt($Number$);]]>
   ```

2. Kod parçacığı dosyasını kaydedin.

3. Bir proje açın ve kod parçacığını ekleyin.

   Kod parçacığı eklenir ve düzenlenebilir değişmez değer değiştirme için vurgulanır. Değerin araç ipucunu görmek için değiştirme parametresinin üzerine gelin.

   ![Visual Studio 'da kod parçacığı değiştirme parametresi araç ipucu](media/snippet-replacement-parameter-tooltip.png)

   > [!TIP]
   > Bir kod parçacığında birden çok değiştirme kablosu parametresi varsa, değerleri değiştirmek için bir defadan diğerine gitmek üzere **Tab** tuşuna basabilirsiniz.

## <a name="import-a-namespace"></a>Ad alanını içeri aktarma

`using`Içeri aktarmalar öğesini ekleyerek bir yönerge (C#) veya `Imports` ifade (Visual Basic) [](code-snippets-schema-reference.md#imports-element)eklemek için bir kod parçacığı kullanabilirsiniz. .NET Framework projeler için, [Başvurular öğesini](code-snippets-schema-reference.md#references-element)kullanarak da projeye bir başvuru ekleyebilirsiniz.

Aşağıdaki XML, System.IO ad alanında yöntemini kullanan bir kod parçacığını gösterir `File.Exists` ve bu nedenle, System.IO ad alanını içeri aktarmak Için **Imports** öğesini tanımlar.

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>File Exists</Title>
      <Shortcut>exists</Shortcut>
    </Header>
    <Snippet>
      <Code Language="CSharp">
        <![CDATA[var exists = File.Exists("C:\\Temp\\Notes.txt");]]>
      </Code>
      <Imports>
        <Import>
          <Namespace>System.IO</Namespace>
        </Import>
      </Imports>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları şema başvurusu](../ide/code-snippets-schema-reference.md)
