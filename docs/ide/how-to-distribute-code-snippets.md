---
title: Kod parçacıklarını uzantı olarak dağıtma
description: Kod parçacıklarını diğer geliştiricilere dağıtmak için Kod Parçacıkları Yöneticisi'ni kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/21/2019
ms.topic: how-to
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: ab7146c9240358ded884f0170d53b9e342b4ebcc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086124"
---
# <a name="how-to-distribute-code-snippets"></a>Nasıl: Kod parçacıklarını dağıtma

Kod parçacıklarınızı arkadaşlarınıza sekleyebilirsiniz ve Kod Parçacıkları Yöneticisi'ni kullanarak kod parçacıklarını kendi **bilgisayarlarına yüklemelerini sekleyebilirsiniz.** Ancak, dağıtacak birden fazla kod parçacığınız varsa veya bunları daha geniş bir şekilde dağıtmak için kod parçacığı dosyalarınızı bir Visual Studio ekleyebilirsiniz. Visual Studio kullanıcılar daha sonra kod parçacıklarını almak için uzantıyı yükleyebilir.

## <a name="prerequisites"></a>Önkoşullar

**VSIX** **Visual Studio proje şablonlarına** erişim elde etmek için Project iş yükünü yükleyin.

![Visual Studio uzantısı geliştirme iş yükü](media/vs-2019/extension-development-workload.png)

## <a name="set-up-the-extension"></a>Uzantıyı ayarlama

Bu yordamda, Kılavuz: Kod parçacığı Merhaba Dünya kod parçacığı oluşturma içinde oluşturulan aynı kod [parçacığını kullanabilirsiniz.](../ide/walkthrough-creating-a-code-snippet.md) Bu makalede kod parçacığı XML'i ve dolayısıyla geri dönüp bir kod parçacığı oluşturmanıza gerek yok.

1. Boş VSIX dosya **şablonundan yeni bir Project** proje oluşturun ve projeyi **TestSnippet olarak ad girin.**

2. **TestSnippet projesinde,** yeni bir XML dosyası ekleyin ve *VBCodeSnippet.snippet olarak çağırabilirsiniz.* İçeriği aşağıdaki XML ile değiştirin:

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

1. Bu **Çözüm Gezgini** proje düğümünü seçin ve Kod Parçacıkları Yöneticisi'nde kod parçacığının adını içeren **bir klasör ekleyin.** Bu durumda **HelloWorldVB olması gerekir.**

2. *.snippet dosyasını* *HelloWorldVB klasörüne* taşıma.

3. **Çözüm Gezgini**'de *.snippet* dosyasını seçin ve  Özellikler penceresinde  Derleme Eylemi'nin **İçerik,** Çıkış Dizinine Kopyala'nın her zaman Kopyala olarak ve **VSIX'e** Dahil Edin'in true olarak ayarlanmış olduğundan emin **olun.** 

### <a name="add-the-pkgdef-file"></a>.pkgdef dosyasını ekleme

::: moniker range="vs-2017"

1. *HelloWorldVB* klasörüne bir metin dosyası ekleyin ve *HelloWorldVB.pkgdef olarak ad girin.* Bu dosya, kayıt defterine belirli anahtarları eklemek için kullanılır. Bu durumda, yeni anahtara yeni bir alt **anahtarHKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Languages\CodeExpansions\Basic** ekler.

::: moniker-end

::: moniker range=">=vs-2019"

1. *HelloWorldVB* klasörüne bir metin dosyası ekleyin ve *HelloWorldVB.pkgdef olarak ad girin.* Bu dosya, kayıt defterine belirli anahtarları eklemek için kullanılır. Bu durumda, yeni anahtara yeni bir alt **anahtarHKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Languages\CodeExpansions\Basic** ekler.

::: moniker-end

2. Aşağıdaki satırları dosyaya ekleyin.

    ```txt
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

    Bu anahtarı incelersiniz, farklı dilleri nasıl belirtmezseniz bunu da incelersiniz.

3. Çözüm Gezgini 'de *.pkgdef* dosyasını seçin ve **Özellikler penceresinde** şunların doğru olduğundan emin olun: 

   - **Derleme Eylemi** İçerik olarak **ayarlanmış**
   - **Çıkış Dizinine Kopyala her** zaman kopyala **olarak ayarlanır**
   - **VSIX'e dahil** etmek true olarak **ayarlanır**

4. *VSIX bildiriminde .pkgdef* dosyasını varlık olarak ekleyin. *source.extension.vsixmanifest* dosyasında Varlıklar sekmesine gidin ve **Yeni'ye** **tıklayın.**

5. Yeni **Varlık Ekle iletişim** kutusunda  Tür olarak **Microsoft.VisualStudio.VsPackage,** dosya sistemi üzerinde  Kaynaktan Dosyaya ve **HelloWorldVB.pkgdef** Yolu 'na (açılan liste görünür) ayarlayın.  

### <a name="test-the-snippet"></a>Kod parçacığını test etmek

1. Artık kod parçacığının deneysel Visual Studio. Deneysel örnek, kod yazmak için Visual Studio ayrı bir dosyanın ikinci kopyasıdır. Geliştirme ortamınızı etkilemeden uzantı üzerinde çalışmanıza olanak sağlar.

2. Projeyi derleme ve hata ayıklamayı başlatma.

   İkinci bir örnek Visual Studio görüntülenir.

3. Deneysel örnekte Araçlar Kod Parçacıkları   >  **Yöneticisi'ne gidin ve** **Dil'i Temel olarak** **ayarlayın.** Klasörlerden *biri olarak HelloWorldVB'i* görüyor ve HelloWorldVB kod parçacığını görmek için klasörü *genişletebilirsiniz.*

4. Kod parçacığını test etmek. Deneysel örnekte bir Visual Basic projesini açın ve kod dosyalarından birini açın. İmlecinizi kodun herhangi bir yerine yerleştirerek sağ tıklayın ve bağlam menüsünde Kod Parçacığı **Ekle'yi seçin.**

5. Klasörlerden biri *olarak HelloWorldVB'i* görüyor olun. Çift tıklayın. **HelloWorldVB** açılan listesinde **bir açılır Kod Parçacığı: HelloWorldVB >** açılır pencereyi görüyor gerekir. **HelloWorldVB açılan** listesinden tıklayın.

   Kod dosyasına aşağıdaki satır eklenir:

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../ide/code-snippets.md)
