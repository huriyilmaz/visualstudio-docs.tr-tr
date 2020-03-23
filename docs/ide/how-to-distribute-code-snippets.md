---
title: Kod parçacıklarını uzantı olarak dağıtma
ms.date: 03/21/2019
ms.topic: conceptual
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 23e77658b2b09f643af18a3f136f5428828cfb5c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591066"
---
# <a name="how-to-distribute-code-snippets"></a>Nasıl yapılır: Kod parçacıklarını dağıtma

Kod parçacıklarınızı arkadaşlarınıza verebilir ve **Code Snippets Manager'ı**kullanarak parçacıkları kendi bilgisayarlarına yüklemelerini sağlayabilirsiniz. Ancak, dağıtacak birkaç parçacık varsa veya bunları daha yaygın olarak dağıtmak istiyorsanız, parçacık dosyalarınızı Visual Studio uzantısına ekleyebilirsiniz. Visual Studio kullanıcıları daha sonra snippets elde etmek için uzantısı yükleyebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

**VSIX Project** proje şablonlarına erişmek için **Visual Studio uzantısı geliştirme** iş yükünü yükleyin.

![Visual Studio uzantı geliştirme iş yükü](media/vs-2019/extension-development-workload.png)

## <a name="set-up-the-extension"></a>Uzantıyı ayarlama

Bu yordamda, Walkthrough oluşturulan aynı Hello World kod parçacığı [kullanacağız: Bir kod snippet oluşturun.](../ide/walkthrough-creating-a-code-snippet.md) Bu makalede, snippet XML sağlar, böylece geri dönmek ve bir parçacık oluşturmak zorunda değilsiniz.

1. **Boş VSIX Projesi** şablonundan yeni bir proje oluşturun ve proje **TestSnippet**adını.

2. **TestSnippet** projesinde, yeni bir XML dosyası ekleyin ve *VBCodeSnippet.snippet*diyoruz. İçeriği aşağıdaki XML ile değiştirin:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <CodeSnippets
        xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
      <CodeSnippet Format="1.0.0">
        <Header>
          <Title>Hello World VB</Title>
          <Shortcut>HelloWorld</Shortcut>
          <Description>Inserts code</Description>
          <Author>MSIT</Author>
          <SnippetTypes>
            <SnippetType>Expansion</SnippetType>
            <SnippetType>SurroundsWith</SnippetType>
          </SnippetTypes>
        </Header>
        <Snippet>
          <Code Language="VB">
            <![CDATA[Console.WriteLine("Hello, World!")]]>
          </Code>
        </Snippet>
      </CodeSnippet>
    </CodeSnippets>
    ```

### <a name="set-up-the-directory-structure"></a>Dizin yapısını ayarlama

1. **Çözüm Gezgini'nde,** proje düğümünü seçin ve snippet'in Kod **Parçacıkları Yöneticisi'nde**olmasını istediğiniz ada sahip bir klasör ekleyin. Bu durumda, **HelloWorldVB**olmalıdır.

2. *.snippet* dosyasını *HelloWorldVB* klasörüne taşıyın.

3. **Solution Explorer'da** *.snippet* dosyasını seçin ve **Özellikler** penceresinde **Yapı Eyleminin** **İçerik**olarak ayarlandıklarından emin olun , **Çıktı Dizinine Kopyala** her **zaman kopyalanır**ve **VSIX'ye dahil** etmek **doğru**olarak ayarlanır.

### <a name="add-the-pkgdef-file"></a>.pkgdef dosyasını ekle

::: moniker range="vs-2017"

1. *HelloWorldVB* klasörüne bir metin dosyası ekleyin ve *helloWorldVB.pkgdef*adını. Bu dosya, kayıt defterine belirli anahtarları eklemek için kullanılır. Bu durumda, **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Languages\CodeExpansions\Basic** tuşu için yeni bir alt anahtar ekler.

::: moniker-end

::: moniker range=">=vs-2019"

1. *HelloWorldVB* klasörüne bir metin dosyası ekleyin ve *helloWorldVB.pkgdef*adını. Bu dosya, kayıt defterine belirli anahtarları eklemek için kullanılır. Bu durumda, **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Languages\CodeExpansions\Basic** tuşu için yeni bir alt anahtar ekler.

::: moniker-end

2. Aşağıdaki satırları dosyaya ekleyin.

    ```txt
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

    Bu anahtarı incelerseniz, farklı dilleri nasıl belirtebileceğinizi görebilirsiniz.

3. **Solution Explorer'da** *.pkgdef* dosyasını seçin ve **Özellikler** penceresinde aşağıdakilerden emin olun:

   - **Yapı Eylemi** **İçerik** olarak ayarlanır
   - **Çıktı Dizini** kopyala her **zaman kopyalamak** için ayarlanır
   - **VSIX dahil** **gerçek** ayarlanır

4. *.pkgdef* dosyasını VSIX bildiriminde bir varlık olarak ekleyin. *source.extension.vsixmanifest* **dosyasında, Varlıklar** sekmesine gidin ve **Yeni'yi**tıklatın.

5. Yeni **Varlık Ekle** iletişim kutusunda, **Microsoft.VisualStudio.VsPackage** **türü,** **dosya sisteminde Dosya**Ya Giden **Kaynak** ve **HelloWorldVB.pkgdef** **Yolunu** (açılır açılır durumda görünmelidir) ayarlayın.

### <a name="test-the-snippet"></a>Parçacığı test edin

1. Artık kod parçacığının Visual Studio'nun deneysel örneğinde çalıştığından emin olabilirsiniz. Deneysel örnek, Visual Studio'nun kod yazmak için kullandığınızdan ayrı ikinci bir kopyasıdır. Geliştirme ortamınızı etkilemeden bir uzantı üzerinde çalışmanızı sağlar.

2. Projeyi oluşturun ve hata ayıklamaya başlayın.

   Visual Studio'nun ikinci bir örneği görüntülenir.

3. Deneysel örnekte, **Tools** > **Code Snippets Manager'a** gidin ve **Dili** **Temel**Olarak ayarlayın. *HelloWorldVB* klasörlerinden biri olarak görmeniz gerekir ve *HelloWorldVB* snippet görmek için klasörü genişletmek gerekir.

4. Parçacığı test edin. Deneme örneğinde, Visual Basic projesini açın ve kod dosyalarından birini açın. İmlecinizi kodda bir yere yerleştirin, sağ tıklatın ve bağlam menüsüne **Ekle Snippet'i**seçin.

5. *HelloWorldVB* klasörlerinden biri olarak görmelisiniz. Çift tıkla. Bir pop-up **Insert Snippet görmelisiniz: HelloWorldVB bir** açılır **helloWorldVB**vardır >. **HelloWorldVB** açılır dosyasını tıklatın.

   Kod dosyasına aşağıdaki satır eklenir:

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../ide/code-snippets.md)
