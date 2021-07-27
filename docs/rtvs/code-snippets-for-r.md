---
title: R için kod parçacıkları
description: Visual Studio R için kod parçacıkları, benzer kodu tekrar tekrar yeniden oluşturmadan kaçınmaya yardımcı olmak için rastgele uzunlukta kod bloklarını hızla eklemek için kısayollar sağlar.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 1ce733049f23fc4c4522475abc0f9f426186d9f4
ms.sourcegitcommit: fdba1b294b94e1f6a8e897810646873422393fff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2021
ms.locfileid: "114680030"
---
# <a name="code-snippets-for-r"></a>R için kod parçacıkları

Visual Studio kod parçacıkları, benzer kodu tekrar tekrar yeniden oluşturmadan kaçınmaya yardımcı olmak için rastgele uzunlukta kod bloklarını hızla eklemek için kısayollar sağlar. Bu Visual Studio için R Araçları (RTVS), Visual Studio koleksiyonuna onlarca yararlı R kod parçacığı ekler.

Bir kod parçacığı eklemek için kod parçacığının kısaltılmış adını yazın (IntelliSense sağlanır) ve eklemek için **Sekme tuşuna** basın.

Bazı basit örnekler:

- ardından `=` tab tuşuna basın ve RTVS bunu atama işlecine `<-` genişlettir.
- ardından `>` Tab yazın ve RTVS bunu kanal `%>%` işleci genişlettir.

Kod parçacıkları karakterlerin karakter tamamlamadan çok daha fazlası olabilir. örneğin işleviyle bir CSV dosyasını okumaya yönelik bir kod parçacığı, adları veya parametreleri `read.csv` hatırlamanızı sağlar:

![Kod parçacığını kullanarak kod parçacığına çağrı ekleme animasyonu read.csv](media/code-snippet-expansion.gif)

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
