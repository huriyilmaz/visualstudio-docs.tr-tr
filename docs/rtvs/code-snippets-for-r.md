---
title: R için kod parçacıkları
description: içinde R kod parçacıkları Visual Studio rastgele uzunlukta kod bloklarını hızla eklemek için kısayollar sağlar ve benzer kodu tekrar tekrar yeniden oluşturmama konusunda yardımcı olur.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: 59228916793e19713784c6f786bf9fbc13e3e73eab31d995c8a536f766a72603
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121269450"
---
# <a name="code-snippets-for-r"></a>R için kod parçacıkları

Visual Studio kod parçacıkları, benzer kodu tekrar tekrar yeniden oluşturmadan kaçınmaya yardımcı olmak için rastgele uzunlukta kod bloklarını hızla eklemek için kısayollar sağlar. Bu Visual Studio için R Araçları (RTVS), Visual Studio koleksiyonuna onlarca yararlı R kod parçacığı ekler.

Bir kod parçacığı eklemek için kod parçacığının kısaltılmış adını yazın (IntelliSense sağlanır) ve eklemek için **Sekme tuşuna** basın.

Bazı basit örnekler:

- ardından `=` Tab yazın ve RTVS bunu atama işlecine `<-` genişlettir.
- ardından `>` Tab tuşuna basın ve RTVS bunu kanal `%>%` işleci olarak genişlettir.

Kod parçacıkları karakterlerin karakter tamamlamadan çok daha fazlası olabilir. örneğin işleviyle bir CSV dosyasını okumaya yönelik bir kod parçacığı, adları veya parametreleri `read.csv` hatırlamanızı sağlar:

![read.csv'a çağrı eklemek için kod parçacığı kullanma animasyonu](media/code-snippet-expansion.gif)

Bu durumda, siz yazarak `readc` IntelliSense bir tamamlama listesi görüntüler. Açılan listeden bu tamamlamanın seçerek Sekme tuşuna **basılarak** sekme `readc` tuşuna **basılarak** kod parçacığı genişletildi. (Bu nedenle, kod parçacığı genişletme genellikle "kod parçacığını yazın ve SEKME tuşuna iki kez basın" olarak düşünebilirsiniz.) Çoğu durumda ilk Sekme IntelliSense seçimini tamamlar ve ikinci Sekme genişletmeyi tetikler.

Kullanılabilir tüm kod parçacıklarını görmek için Araçlar Kod Parçacıkları Yöneticisi iletişim kutusunu ( Ctrl K , B ) açın ve Dil için  >    +  **R'yi** **seçin.** Açıklamaları ve kısayol metnini görmek için grupları genişletin ve tek tek kod parçacıklarını seçin:

![R için kod parçacıkları iletişim kutusu](media/code-snippet-dialog.png)

Özel kod parçacıkları oluşturmak için, Kılavuz: Kod parçacığı [oluşturma yönergelerini izleyin.](../ide/walkthrough-creating-a-code-snippet.md) Sonuç olarak, kod parçacığı yalnızca bir XML dosyasıdır. Örneğin, aşağıdaki kod kanal işlemi için kod parçacığıdır `>` (kısayol):

```xml
<?xml version="1.0" encoding="utf-8" ?>
<CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>Dplyr pipe</Title>
      <Shortcut>&gt;</Shortcut>
      <Description>Code snippet for '%&gt;%' operator</Description>
      <Author>Microsoft Corporation</Author>
      <SnippetTypes>
        <SnippetType>Expansion</SnippetType>
       </SnippetTypes>
    </Header>
    <Snippet>
      <Code Language="R">
        <![CDATA[ %>% $end$]]>
      </Code>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

Tüm kod parçacıkları için XML dosyaları RTVS ile yüklenir; Kod **Parçacıkları** Yöneticisi'nde **Konum alanı** yolu sağlar. Ayrıca bunları [src/Package/Impl/Snippets](https://github.com/Microsoft/RTVS/tree/master/src/Package/Impl/Snippets)GitHub rtvs kaynak kodunda da bulabilirsiniz.
