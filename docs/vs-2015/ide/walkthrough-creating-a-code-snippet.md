---
title: 'İzlenecek yol: kod parçacığı oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f3cf8d0cfd3119113247dedf7723e02fca9634a3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662643"
---
# <a name="walkthrough-creating-a-code-snippet"></a>İzlenecek Yol: Kod Parçacığı Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yalnızca birkaç adımdan oluşan bir kod parçacığı oluşturabilirsiniz. Yapmanız gereken tek şey bir XML dosyası oluşturur, uygun öğeleri doldurur ve kodunuzu buna ekler. Ayrıca, kodunuza başvurular ve değiştirme parametreleri de ekleyebilirsiniz. Kod parçacıkları yöneticisinde (**Araçlar/kod parçacıkları Yöneticisi**) içeri aktar düğmesini kullanarak kod parçacığını Visual Studio yüklemenize ekleyebilirsiniz.

> [!TIP]
> Kod parçacıklarını daha kolay yazma hakkında daha fazla bilgi için, CodePlex Web sitesinde [kod parçacığı Düzenleyicisi](http://go.microsoft.com/fwlink/?LinkId=251033)gibi topluluk araçları arayın.

## <a name="snippet-template"></a>Kod parçacığı şablonu
 Temel kod parçacığı şablonu aşağıda verilmiştir:

```
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets
    xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
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

### <a name="to-create-a-code-snippet"></a>Kod parçacığı oluşturmak için

1. Visual Studio 'da yeni bir XML dosyası oluşturun ve yukarıda gösterilen şablonu ekleyin.

2. Kod parçacığının başlığını (örneğin, "Merhaba Dünya VB") Başlık öğesine girin.

3. Kod öğesinin Diller özniteliğinde parçacığın dilini girin. Bu örnekte, "VB" kullanın.

4. Kod öğesinin içindeki CDATA bölümüne kod ekleyin, örneğin:

    ```
    <Code Language="VB">
        <![CDATA[Console.WriteLine("Hello, World!")]]>
    </Code>

    ```

5. Kod parçacığını Vbcodeparçacığın. kod parçacığı olarak kaydedin.

### <a name="to-add-a-code-snippet-to-visual-studio"></a>Visual Studio 'ya kod parçacığı eklemek için

1. Kod parçacıkları Yöneticisi 'Ni kullanarak Visual Studio yüklemenize kendi kod parçacıklarını ekleyebilirsiniz. Kod parçacıkları yöneticisini açın (**Araçlar/kod parçacıkları Yöneticisi**).

2. **Al** düğmesine tıklayın.

3. Kod parçacığını önceki yordamda kaydettiğiniz konuma gidin, seçin ve **Aç**' a tıklayın.

4. **Kod parçacığını Içeri aktar** iletişim kutusu açılarak sağ bölmedeki seçimlerden parçacığın nereye ekleneceğini seçmenizi ister. Seçimlerinizden biri **kod**parçacıklarında olmalıdır. Seçin ve **son**' a ve ardından **Tamam**' a tıklayın.

5. Kod parçacığı şu konuma kopyalanır:

     `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippets`

6. Bir Visual Basic projesi açıp bir kod dosyası açarak kod parçacığınızı test edin. Dosyada bağlam menüsünde kod **parçacığı Ekle** ' ye, sonra da **kod**parçacıklarında tıklayın. **Visual Basic kod parçacığı My**adlı bir kod parçacığı görmeniz gerekir. Çift tıklayın.

7. Koda `Console.WriteLine("Hello, World!")` eklendiğini görmeniz gerekir.

### <a name="adding-description-and-shortcut-fields"></a>Açıklama ve kısayol alanları ekleme

1. Açıklama alanları, kod parçacıkları yöneticisinde görüntülenirken kod parçacığınızı hakkında daha fazla bilgi verir. Kısayol, kod parçacığınızı eklemek için kullanıcıların yazsaykullandığı bir etikettir. @No__t_0 dosyasını açarak eklemiş olduğunuz kod parçacığını düzenleyin.

2. Üstbilgi öğesine yazar ve açıklama öğeleri ekleyin ve bunları içine girin.

3. Header öğesi şuna benzer görünmelidir:

    ```
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
    </Header>

    ```

4. Kod parçacıkları yöneticisini açın ve kod parçacığını seçin. Sağ bölmede, açıklama ve yazar alanlarının artık doldurulduğunu görmeniz gerekir.

5. Kısayol eklemek için, yazar ve açıklama öğesinin yanına bir kısayol öğesi ekleyin:

    ```
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
        <Shortcut>hello</Shortcut>
    </Header>

    ```

6. Kod parçacığı dosyasını yeniden kaydedin.

7. Kısayolu test etmek için bir Visual Basic projesi açın ve bir kod dosyası açın. Dosyaya `hello` yazın ve TAB tuşuna basın. Kod parçacığı kodu eklenmelidir.

### <a name="to-add-references-and-imports"></a>Başvurular ve Içeri aktarmalar eklemek için

1. Visual Basic parçacıkları ile, Başvurular öğesini kullanarak bir projeye başvuru ekleyebilir ve Içeri aktarmalar öğesini kullanarak bir Içeri aktarmalar bildirimi ekleyebilirsiniz. (Diğer dillerdeki kod parçacıkları bu özelliğe sahip değildir.) Örneğin, kod örnekteki `Console.WriteLine` `MessageBox.Show` olarak değiştirirseniz, System. Windows. Forms. dll derlemesini projeye eklemeniz gerekebilir.

2. Kod parçacığınızı açın.

3. Kod parçacığı öğesinin altına References öğesini ekleyin:

    ```
    <References>
        <Reference>
            <Assembly>System.Windows.Forms.dll</Assembly>
        </Reference>
    </References>

    ```

4. Kod parçacığı öğesinin altına Imports öğesini ekleyin:

    ```
    <Imports>
        <Import>
           <Namespace>System.Windows.Forms</Namespace>
        </Import>
    </Imports>

    ```

5. CDATA bölümünü aşağıdaki şekilde değiştirin:

    ```
    <![CDATA[MessageBox.Show("Hello, World!")]]>
    ```

6. Kod parçacığını kaydedin.

7. Bir Visual Basic projesi açın ve kod parçacığını ekleyin.

8. Kod dosyasının en üstünde bir Içeri aktarmalar açıklaması görürsünüz:

    ```
    Imports System.Windows.Forms

    ```

9. Projenin özelliklerine bakın. Başvurular sekmesi, System. Windows. Forms. dll ' ye bir başvuru içerir.

### <a name="adding-replacements"></a>Değişiklik ekleme

1. Kod parçacılarınızın bölümlerinin Kullanıcı tarafından değiştirilmesini isteyebilirsiniz, örneğin bir değişken eklerseniz ve kullanıcının değişkeni geçerli projede bir ile değiştirmesini istiyorsanız. İki tür değiştirme sağlayabilirsiniz: değişmez değerler ve nesneler. Değişmez değerler bazı tür dizelerdir (dize sabit değerleri, değişken adları veya sayısal değerlerin dize temsilleri). Nesneler, bir dize dışında bazı tür örnekleridir. Bu yordamda, bir sabit değer değişimi ve bir nesne değişikliği bildirir ve kodu bu değişikliklere başvuracak şekilde değiştirirsiniz.

2. Kod parçacığınızı açın.

3. Bu örnek, bir SQL bağlantı dizesi kullanır, bu nedenle uygun başvuruları eklemek için Içeri aktarmaları ve başvurular öğelerini değiştirmeniz gerekir:

    ```
    <References>
        <Reference>
            <Assembly>System.Data.dll</Assembly>
        </Reference>
        <Reference>
            <Assembly>System.Xml.dll</Assembly>
        </Reference>
    </References>
    <Imports>
        <Import>
            <Namespace>System.Data</Namespace>
        </Import>
        <Import>
            <Namespace>System.Data.SqlClient</Namespace>
        </Import>
    </Imports>

    ```

4. SQL bağlantı dizesi için bir sabit değer değişikliği bildirmek için, kod parçacığı öğesinin altına bir bildirim öğesi ekleyin ve bu öğenin KIMLIĞI, araç ipucu ve değiştirme için varsayılan değer için alt öğeler içeren bir sabit değer öğesi ekleyin:

    ```
    <Declarations>
        <Literal>
            <ID>SqlConnString</ID>
            <ToolTip>Replace with a SQL connection string.</ToolTip>
            <Default>"SQL connection string"</Default>
        </Literal>
    </Declarations>

    ```

5. SQL bağlantısı için bir nesne değişikliği bildirmek için, bildirimler öğesinin içine bir nesne öğesi ekleyin ve KIMLIK, nesne türü, araç ipucu ve varsayılan değer için alt öğeler ekleyin. Elde edilen bildirimler öğesi şöyle görünmelidir:

    ```
    <Declarations>
        <Literal>
            <ID>SqlConnString</ID>
            <ToolTip>Replace with a SQL connection string.</ToolTip>
            <Default>"SQL connection string"</Default>
        </Literal>
        <Object>
            <ID>SqlConnection</ID>
            <Type>System.Data.SqlClient.SqlConnection</Type>
            <ToolTip>Replace with a connection object in your application.</ToolTip>
            <Default>dcConnection</Default>
        </Object>
    </Declarations>
    ```

6. Kod bölümünde, çevreleyen $ işaretleriyle birlikte bulunan değişikliklere başvurabilirsiniz, örneğin `$replacement$`:

    ```
    <Code Language="VB" Kind="method body">
        <![CDATA[Dim daCustomers As SqlDataAdapter
            Dim selectCommand As SqlCommand

            daCustomers = New SqlClient.SqlDataAdapter()
            selectCommand = new SqlClient.SqlCommand($SqlConnString$)
            daCustomers.SelectCommand = selectCommand
            daCustomers.SelectCommand.Connection = $SqlConnection$]]>
    </Code>
    ```

7. Kod parçacığını kaydedin.

8. Bir Visual Basic projesi açın ve kod parçacığını ekleyin.

9. Kod aşağıdaki gibi görünmelidir, burada `SQL connection string` ve `dcConnection` değiştirmeler Açık Turuncu renkle vurgulanır. Bir diğerine gitmek için TAB tuşuna basın.

    ```
    Dim daCustomers As SqlDataAdapter
    Dim selectCommand As SqlCommand

    daCustomers = New SqlClient.SqlDataAdapter()
    selectCommand = New SqlClient.SqlCommand("SQL connection string")
    daCustomers.SelectCommand = selectCommand
    daCustomers.SelectCommand.Connection = dcConnection

    ```

## <a name="see-also"></a>Ayrıca Bkz.
 [Kod Parçacıkları Şema Başvurusu](../ide/code-snippets-schema-reference.md)
