---
title: 'İzlenecek yol: Kod parçacığı oluşturma'
description: 'Üç adımda kod parçacığı oluşturma hakkında bilgi edinebilirsiniz: XML dosyası oluşturma, uygun öğeleri doldurma ve kodunuzu buna ekleme.'
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
ms.technology: vs-ide-general
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: f04ba5610783fbe940504c83c387aa3aade90f24ad8bb1aaf1cecde945f169f1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121258518"
---
# <a name="walkthrough-create-a-code-snippet"></a>İzlenecek yol: Kod parçacığı oluşturma

Yalnızca birkaç adımda kod parçacığı oluşturabilirsiniz. Tek ihtiyacınız olan bir XML dosyası oluşturmak, uygun öğeleri doldurmak ve kodunuzu buna eklemektir. İsteğe bağlı olarak değiştirme parametrelerini ve proje başvurularını kullanabilirsiniz. Kod Parçacıkları Yöneticisi'nde Visual Studio düğmesini kullanarak  kod parçacığını yüklemenize **aktarın** (**Araçlar**  >  **Kod Parçacıkları Yöneticisi**).

## <a name="snippet-template"></a>Kod parçacığı şablonu

Aşağıdaki XML temel kod parçacığı şablonudur:

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

1. Dosyanın içinde yeni bir XML Visual Studio ve yukarıda gösterilen şablonu ekleyin.

2. Başlık öğesinde kod parçacığının **başlığını** doldurun. Karekök **başlığını kullanın.**

3. Kod öğesinin Language özniteliğinde **kod** parçacığının **dilini** doldurun. C# için **CSharp** kullanın, Visual Basic **VB** kullanın ve C++ için **CPP kullanın.**

   > [!TIP]
   > Tüm kullanılabilir dil değerlerini görmek için Kod parçacıkları [şema başvuru sayfasındaki](code-snippets-schema-reference.md#attributes) Kod öğesi [öznitelikleri bölümüne göz](code-snippets-schema-reference.md) atın.

4. Kod parçacığı kodunu **Code öğesinin içindeki CDATA** **bölümüne** ekleyin.

   C# için:

   ```xml
   <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt(16);]]>
   </Code>
   ```

   Veya Visual Basic:

   ```xml
   <Code Language="VB">
       <![CDATA[Dim root = Math.Sqrt(16)]]>
   </Code>
   ```

   > [!NOTE]
   > Kod parçacığının **CDATA** bölümünde kod satırlarının nasıl girintili veya biçimlendirilmiş olması gerektiğini belirtemezseniz. Eklemeden sonra dil hizmeti eklenen kodu otomatik olarak biçimler.

5. Kod parçacığını *SquareRoot.snippet olarak* kaydedin (istediğiniz yere kaydedebilirsiniz).

## <a name="import-a-code-snippet"></a>Kod parçacığını içeri aktarma

1. Kod Parçacıkları Yöneticisi'ni kullanarak Visual Studio kod parçacığını **yüklemenize aktarabilirsiniz.** Araç Kod Parçacıkları **Yöneticisi'ni**  >  **seçerek açın.**

2. İçeri Aktar **düğmesine** tıklayın.

3. Kod parçacığını önceki yordamda kaydeden konuma gidin, seçin ve Aç'a **tıklayın.**

4. Kod **Parçacığını İçeri** Aktar iletişim kutusu açılır ve sağ bölmede yer alan seçeneklerden kod parçacığını nereye ekleyebilirsiniz? Seçeneklerden biri Kod **Parçacıklarım olacaktır.** Seçin ve **Son'a ve** ardından Tamam'a **tıklayın.**

5. Kod parçacığı, kod diline bağlı olarak aşağıdaki konumlardan biri ile kopyalanır:

   ::: moniker range="vs-2017"

   *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual C#\Kod Parçacıklarım*  
   *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual Basic\Kod Parçacıklarım*

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual C#\Kod Parçacıklarım*  
   *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual Basic\Kod Parçacıklarım*

   ::: moniker-end

6. C# veya Visual Basic projesini açarak kod parçacığınızı test etmek. Düzenleyicide bir kod dosyası açıkken sağ tıklama **menüsünden Kod** Parçacıkları Kod Parçacığı Ekle'yi ve ardından  >   Kod **Parçacıklarım'ı seçin.** Karekök adlı bir kod **parçacığı görüyor gerekir.** Çift tıklayın.

   Kod parçacığı kodu, kod dosyasına eklenir.

## <a name="description-and-shortcut-fields"></a>Açıklama ve kısayol alanları

::: moniker range="vs-2017"

1. Açıklama alanları, Kod Parçacıkları Yöneticisi'nde görüntü zaman kod parçacığınız hakkında daha fazla bilgi sağlar. Kısayol, kullanıcıların kod parçacığınızı eklemek için yazarak oluştura bir etikettir. *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets \\ [Visual C# veya Visual Basic]\Kod Parçacığım\SquareRoot.snippet* dosyasını açarak ekley istediğiniz kod parçacığını düzenleyin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Açıklama alanları, Kod Parçacıkları Yöneticisi'nde görüntü zaman kod parçacığınız hakkında daha fazla bilgi sağlar. Kısayol, kullanıcıların kod parçacığınızı eklemek için yazarak oluştura bir etikettir. *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets \\ [Visual C# veya Visual Basic]\Kod Parçacığım\SquareRoot.snippet* dosyasını açarak ekley istediğiniz kod parçacığını düzenleyin.

::: moniker-end

   > [!TIP]
   > Dosyayı, dosyanın yerleştiril olduğu dizinde Visual Studio, dosyayı dizine yeniden Visual Studio.

2. Header **öğesine Author** ve **Description** **öğelerini** ekleyin ve bunları doldurun.

3. **Header öğesi** şuna benzer şekilde görünür:

   ```xml
   <Header>
       <Title>Square Root</Title>
       <Author>Myself</Author>
       <Description>Calculates the square root of 16.</Description>
   </Header>
   ```

4. Kod Parçacıkları **Yöneticisi'ni açın** ve kod parçacığınızı seçin. Sağ bölmede Açıklama ve Yazar **alanlarının** **doldurulduğundan** dikkat edersiniz.

   ![Kod Parçacığı Yöneticisi'nde kod parçacığı açıklaması](media/code-snippet-description-author.png)

5. Kısayol eklemek için Header **öğesinin içinde bir Shortcut** **öğesi** ekleyin:

   ```xml
   <Header>
      <Title>Square Root</Title>
      <Author>Myself</Author>
      <Description>Calculates the square root of 16.</Description>
      <Shortcut>sqrt</Shortcut>
    </Header>
   ```

6. Kod parçacığı dosyasını yeniden kaydedin.

7. Kısayolu test etmek için daha önce kullanılan projeyi açın, düzenleyicide **sqrt** yazın ve **Sekme** tuşuna basın (bir kez Visual Basic, C# için iki kez).

   Kod parçacığı kodu eklenir.

## <a name="replacement-parameters"></a>Değiştirme parametreleri

Kod parçacığının bölümlerinin kullanıcı tarafından değiştirilmesini istiyor olabilir. Örneğin, kullanıcının geçerli projesinde bir değişken adı ile değiştirmesini istiyor olabilir. İki tür değiştirme sebilirsiniz: değişmezler ve nesneler. Kod [parçacığının](code-snippets-schema-reference.md#literal-element) içinde yer alan ancak koda eklendikten sonra (örneğin, bir dize veya sayısal değer) özelleştirilen bir kod parçasının yerini belirlemek için Literal öğesini kullanın. Kod [parçacığı için](code-snippets-schema-reference.md#object-element) gerekli olan ancak büyük olasılıkla kod parçacığının dışında tanımlanacak bir öğeyi (örneğin, nesne örneği veya denetim) tanımlamak için Object öğesini kullanın.

1. Kullanıcının karekökünü hesaplamak için sayısını kolayca değiştirmesini sağlamak için *SquareRoot.snippet* dosyasının **Snippet** öğesini aşağıdaki gibi değiştirin:

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

   Değişmez değiştirme için bir kimlik ( ) verildiğine dikkat `Number` eder. Bu kimlik, kod parçacığının içinde, onu çevreleyen karakterlerle `$` başvurur:

   ```xml
   <![CDATA[double root = Math.Sqrt($Number$);]]>
   ```

2. Kod parçacığı dosyasını kaydedin.

3. Bir proje açın ve kod parçacığını ekler.

   Kod parçacığı eklenir ve değiştirme için düzenlenebilir değişmez değişmez kod vurgulanır. Değerin araç ipucuna bakarak değiştirme parametresinin üzerine gelin.

   ![Kod parçacığı değiştirme parametresi araç ipucu Visual Studio](media/snippet-replacement-parameter-tooltip.png)

   > [!TIP]
   > Bir kod parçacığında birden fazla değiştirilebilir parametre varsa  Sekme tuşuna basarak değerleri değiştirmek için bir parametreden diğer parametreye geçebilirsiniz.

## <a name="import-a-namespace"></a>Ad alanını içeri aktarma

Imports öğesini dahil etmek üzere bir yönerge `using` (C#) veya deyimi (Visual Basic) eklemek için kod `Imports` [parçacığı kullanabilirsiniz.](code-snippets-schema-reference.md#imports-element) Daha .NET Framework için, References öğesini kullanarak projeye bir başvuru [da ebilirsiniz.](code-snippets-schema-reference.md#references-element)

Aşağıdaki XML, System.IO ad alanı içinde yöntemini kullanan bir kod parçacığını gösterir ve bu nedenle, System.IO ad alanını `File.Exists` içeri System.IO tanımlar. 

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
