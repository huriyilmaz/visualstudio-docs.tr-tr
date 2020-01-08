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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591066"
---
# <a name="how-to-distribute-code-snippets"></a>Nasıl yapılır: kod parçacıklarını dağıtma

Kod parçacıklarında Arkadaşlarınıza kod parçacıklarını verebilir ve **kod parçacıkları Yöneticisi 'ni**kullanarak kendi bilgisayarlarına kod parçacıkları yükleyebilirsiniz. Ancak, dağıtılacak birkaç kod parçacığına sahipseniz veya bunları daha yaygın olarak dağıtmak istiyorsanız, kod parçacığı dosyalarınızı bir Visual Studio uzantısına dahil edebilirsiniz. Visual Studio kullanıcıları daha sonra kod parçacıklarını almak için uzantıyı yükleyebilir.

## <a name="prerequisites"></a>Prerequisites

**VSIX proje** projesi şablonlarına erişim sağlamak Için **Visual Studio uzantısı geliştirme** iş yükünü yükler.

![Visual Studio uzantısı geliştirme iş yükü](media/vs-2019/extension-development-workload.png)

## <a name="set-up-the-extension"></a>Uzantıyı ayarlama

Bu yordamda, [Izlenecek yol: kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md)' da oluşturulan Merhaba Dünya kod parçacığını kullanacaksınız. Bu makalede kod parçacığı XML 'SI sağlanmıştır, bu nedenle geri dönüp bir kod parçacığı oluşturmanız gerekmez.

1. **Boş VSIX proje** şablonundan yeni bir proje oluşturun ve proje **testparçacığını**adlandırın.

2. **Testparçacığının** projesinde yenı bir XML dosyası ekleyin ve bu dosyayı *vbcodeparçacığın. parçacığını*çağırın. İçeriği aşağıdaki XML ile değiştirin:

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

1. **Çözüm Gezgini**' de, proje düğümünü seçin ve **kod parçacıkları yöneticisinde, kod**parçacığında olmasını istediğiniz ada sahip bir klasör ekleyin. Bu durumda, **Merhaba Worldvb**olmalıdır.

2. *. Parçacığının* dosyasını *HelloWorldVB* klasörüne taşıyın.

3. **Çözüm Gezgini** *. kod parçacığı* dosyasını seçin ve **Özellikler** penceresinde **derleme eyleminin** **içerik**olarak ayarlandığından emin olun, **Çıkış Dizinine Kopyala** özelliği **her zaman Kopyala**olarak ayarlanır ve **VSIX 'e dahil et** özelliği **true**olarak ayarlanır.

### <a name="add-the-pkgdef-file"></a>. Pkgdef dosyasını ekleme

::: moniker range="vs-2017"

1. *Merhaba worldvb* klasörüne bir metin dosyası ekleyin ve *Merhaba worldvb. pkgdef*olarak adlandırın. Bu dosya, kayıt defterine belirli anahtarlar eklemek için kullanılır. Bu durumda, **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\15.0\Languages\CodeExpansions\Basic** anahtarına yeni bir alt anahtar ekler.

::: moniker-end

::: moniker range=">=vs-2019"

1. *Merhaba worldvb* klasörüne bir metin dosyası ekleyin ve *Merhaba worldvb. pkgdef*olarak adlandırın. Bu dosya, kayıt defterine belirli anahtarlar eklemek için kullanılır. Bu durumda, **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\16.0\Languages\CodeExpansions\Basic** anahtarına yeni bir alt anahtar ekler.

::: moniker-end

2. Dosyasına aşağıdaki satırları ekleyin.

    ```txt
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

    Bu anahtarı incelerseniz, farklı dillerin nasıl gösterileceğini görebilirsiniz.

3. **Çözüm Gezgini** *. pkgdef* dosyasını seçin ve **Özellikler** penceresinde şunları yaptığınızdan emin olun:

   - **Derleme eylemi** **içerik** olarak ayarlandı
   - **Çıkış Dizinine Kopyala** , **her zaman Kopyala** olarak ayarlandı
   - **VSIX 'e Ekle** **doğru** olarak ayarlandı

4. *. Pkgdef* dosyasını VSIX bildiriminde bir varlık olarak ekleyin. *Source. Extension. valtmanifest* dosyasında, **varlıklar** sekmesine gidin ve **Yeni**' ye tıklayın.

5. **Yeni varlık Ekle** iletişim kutusunda, **türü** **Microsoft. VisualStudio. VSPackage**, **FileSystem üzerindeki dosya**için **kaynak** ve **Merhaba worldvb. pkgdef** **yolunu** (açılan menüde görünmelidir) ayarlayın.

### <a name="test-the-snippet"></a>Kod parçacığını test etme

1. Artık kod parçacığının Visual Studio 'nun deneysel örneğinde çalıştığından emin olabilirsiniz. Deneysel örnek, Visual Studio 'nun kod yazmak için kullandığınız bir ikinci kopyasıdır. Geliştirme ortamınızı etkilemeden bir uzantı üzerinde çalışmanıza olanak sağlar.

2. Projeyi oluşturmak ve hata ayıklamaya başlayın.

   Visual Studio 'nun ikinci bir örneği görüntülenir.

3. Deneysel örnekte, **araçlar** > **kod parçacıkları Yöneticisi** ' ne gidin ve **dili** **temel**olarak ayarlayın. Bir klasörden birine *Merhaba Worldvb* görmeniz gerekir ve *Merhaba worldvb* kod parçacığını görmek için klasörü genişletmeniz gerekir.

4. Kod parçacığını test edin. Deneysel örnekte, bir Visual Basic projesi açın ve kod dosyalarından birini açın. İmlecinizi kodda bir yere yerleştirin, sağ tıklayın ve bağlam menüsünde kod **parçacığı Ekle**' yi seçin.

5. Bir klasörden biri olarak *Merhaba Worldvb* görmeniz gerekir. Çift tıklatın. Açılan bir **ekleme kod parçacığı** görmeniz gerekir: bir açılan Merhaba çalışma parçacığı, bir açılan **helloworldvb**>. **Merhaba Worldvb** açılan listesine tıklayın.

   Kod dosyasına aşağıdaki satır eklenir:

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../ide/code-snippets.md)
