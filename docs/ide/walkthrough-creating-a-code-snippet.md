---
title: 'İzlenecek yol: Kod parçacığı oluşturma'
ms.date: 06/10/2019
ms.topic: conceptual
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
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2554729be8f3b9697d1407befd68cbb21fac10dd
ms.sourcegitcommit: 992dd075e65b5f3adefc1ff758975298c47381e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2020
ms.locfileid: "80435046"
---
# <a name="walkthrough-create-a-code-snippet"></a>İzlenecek yol: Kod parçacığı oluşturma

Yalnızca birkaç adımda bir kod parçacığı oluşturabilirsiniz. Tek yapmanız gereken bir XML dosyası oluşturmak, uygun öğeleri doldurmak ve kodunuzu eklemektir. İsteğe bağlı olarak değiştirme parametrelerini ve proje başvurularını kullanabilirsiniz. **Kod Parçacıkları Yöneticisi** **(Tools** > **Code Snippets Manager)** adresindeki **Alma** düğmesini kullanarak snippet'i Visual Studio kurulumunuza aktarın.

## <a name="snippet-template"></a>Parçacık şablonu

Aşağıdaki XML temel parçacık şablonudur:

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

1. Visual Studio'da yeni bir XML dosyası oluşturun ve yukarıda gösterilen şablonu ekleyin.

2. **Başlık** öğesindeki parçacık başlığını doldurun. **Kare Kök**başlığını kullanın.

3. **Kod** öğesinin **Dil** özniteliğindeki parçacık dilini doldurun. C# için Visual Basic için **CSharp,** **VB**ve C++, **CPP**kullanın.

   > [!TIP]
   > Kullanılabilir tüm dil değerlerini görmek için, Kod parçacıkları [şeması başvuru](code-snippets-schema-reference.md) sayfasındaki Kod öğesi [öznitelikleri bölümüne](code-snippets-schema-reference.md#attributes) göz atın.

4. **Kod** öğesinin içindeki **CDATA** bölümündeki parçacık kodunu ekleyin.

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
   > Bir kod parçasının **CDATA** bölümündeki kod satırlarının nasıl girintisi veya biçimlendirilmesi gerektiğini belirtemezsiniz. Ekleme üzerine, dil hizmeti eklenen kodu otomatik olarak biçimlendirin.

5. *Snippet'i SquareRoot.snippet* olarak kaydedin (istediğiniz yere kaydedebilirsiniz).

## <a name="import-a-code-snippet"></a>Kod snippet alma

1. **Code Snippets Manager'ı**kullanarak Visual Studio kurulumunuza bir parçacık aktarabilirsiniz. **Araçlar** > **Kodu Snippets Manager**seçerek açın.

2. **İçe Aktar** düğmesini tıklatın.

3. Önceki yordamda kod parçacıklarını kaydettiğiniz konuma gidin, seçin ve **Aç'ı**tıklatın.

4. **İçe Alma Kodu Snippet** iletişim kutusu açılır ve sağ bölmedeki seçeneklerden parçacığı nereye ekleyeceğinizi seçmenizi ister. Seçeneklerden biri **Benim Kodu Snippets**olmalıdır. Seçin ve **Bitir'e**tıklayın, sonra **Tamam**.

5. Parçacık, kod diline bağlı olarak aşağıdaki konumlardan birine kopyalanır:

   ::: moniker range="vs-2017"

   *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual C#\My Code Snippets*
    *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual Basic\My Code Snippets*

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual C#\My Code Snippets*
    *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual Basic\My Code Snippets*

   ::: moniker-end

6. C# veya Visual Basic projesini açarak parçacığınızı test edin. Düzenleyicide açık bir kod dosyasıyla, sağ tıklatma menüsünden **Snippets** > **Ekle Snippet'i** seçin, ardından **Kod Parçacıklarım.** **Kare Kök**adlı bir parçacık görmelisiniz. Çift tıkla.

   Parçacık kodu kod dosyasına eklenir.

## <a name="description-and-shortcut-fields"></a>Açıklama ve kısayol alanları

::: moniker range="vs-2017"

1. Açıklama alanları, Kod Parçacıkları Yöneticisi'nde görüntülendiğinde kod parçacığınız hakkında daha fazla bilgi verir. Kısayol, kullanıcıların parçacıkınızı eklemek için yazabilecekleri bir etikettir. Eklediğiniz parçayı *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\\[Visual C# or Visual Basic]\My Code Snippet\SquareRoot.snippet*dosyasını açarak düzenleme .

::: moniker-end

::: moniker range=">=vs-2019"

1. Açıklama alanları, Kod Parçacıkları Yöneticisi'nde görüntülendiğinde kod parçacığınız hakkında daha fazla bilgi verir. Kısayol, kullanıcıların parçacıkınızı eklemek için yazabilecekleri bir etikettir. Eklediğiniz parçayı *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\\[Visual C# or Visual Basic]\My Code Snippet\SquareRoot.snippet*dosyasını açarak düzenleme .

::: moniker-end

   > [!TIP]
   > Visual Studio'nun yerleştirildiği dizindeki dosyayı düzenlediğiniz için Visual Studio'ya yeniden aktarmanız gerekmez.

2. **Üstbilgi** öğesine **Yazar** ve **Açıklama** öğelerini ekleyin ve doldurun.

3. **Üstbilgi** öğesi şuna benzer:

   ```xml
   <Header>
       <Title>Square Root</Title>
       <Author>Myself</Author>
       <Description>Calculates the square root of 16.</Description>
   </Header>
   ```

4. Kod **Parçacıkları Yöneticisi'ni** açın ve kod parçacığınızı seçin. Sağ bölmede, **Açıklama** ve **Yazar** alanlarının artık dolduruladığını unutmayın.

   ![Kod Snippet Yöneticisi'nde kod snippet açıklaması](media/code-snippet-description-author.png)

5. Kısayol eklemek için **Üstbilgi** öğesine bir **Kısayol** öğesi ekleyin:

   ```xml
   <Header>
      <Title>Square Root</Title>
      <Author>Myself</Author>
      <Description>Calculates the square root of 16.</Description>
      <Shortcut>sqrt</Shortcut>
    </Header>
   ```

6. Parçacık dosyasını yeniden kaydedin.

7. Kısayolu test etmek için, daha önce kullandığınız projeyi açın, editöre **sqrt** yazın ve **Sekme'ye** basın (Visual Basic için bir kez, C#için iki kez).

   Parçacık kodu eklenir.

## <a name="replacement-parameters"></a>Değiştirme parametreleri

Bir kod parçasının parçalarının kullanıcı tarafından değiştirilmesini isteyebilirsiniz. Örneğin, kullanıcının bir değişken adını geçerli projesinde bir adla değiştirmesini isteyebilirsiniz. İki tür değiştirme sağlayabilirsiniz: gerçek ve nesneler. Tamamen parçacık içinde bulunan ancak büyük olasılıkla koda (örneğin, bir dize veya sayısal değer) ekildikten sonra özelleştirilmiş bir kod parçasının yerine birini tanımlamak için [Literal öğesini](code-snippets-schema-reference.md#literal-element) kullanın. Nesne [öğesini,](code-snippets-schema-reference.md#object-element) kod parçacığı tarafından gerekli olan ancak snippet'in kendisi dışında (örneğin, nesne örneği veya denetim) tanımlanması muhtemel bir öğeyi tanımlamak için kullanın.

1. Kullanıcının kare kökünü hesaplamak için sayıyı kolayca değiştirebilmesini sağlamak *için, SquareRoot.snippet* dosyasının **Snippet** öğesini aşağıdaki gibi değiştirin:

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

   Gerçek değiştirmeye bir kimlik verildiğine`Number`dikkat edin ( ). Bu kimlik, kod parçacığının içinden karakterlerle `$` çevreleyerek başvurulur:

   ```xml
   <![CDATA[double root = Math.Sqrt($Number$);]]>
   ```

2. Parçacık dosyasını kaydedin.

3. Bir proje açın ve parçacığı ekleyin.

   Kod snippet eklenir ve değiştirilebilir için editable literal vurgulanır. Değerin takım ucunu görmek için değiştirme parametresinin üzerine titreyin.

   ![Visual Studio'da kod snippet değiştirme parametresi araç ucu](media/snippet-replacement-parameter-tooltip.png)

   > [!TIP]
   > Bir snippet'te birden fazla değiştirilebilir parametre varsa, değerleri değiştirmek için biri birinden diğerine gitmek için **Sekme** tuşuna basabilirsiniz.

## <a name="import-a-namespace"></a>Ad alanı alma

Bir `using` yönerge (C#) veya `Imports` deyim (Visual Basic) eklemek için Bir kod snippet kullanabilirsiniz. [Imports element](code-snippets-schema-reference.md#imports-element) .NET Framework projeleri [için, Referanslar öğesini](code-snippets-schema-reference.md#references-element)kullanarak projeye bir referans da ekleyebilirsiniz.

Aşağıdaki XML, System.IO ad alanında yöntemi `File.Exists` kullanan bir kod parçacığı gösterir ve bu nedenle, System.IO ad alanını almak için İçeri **aktarım** öğesini tanımlar.

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
