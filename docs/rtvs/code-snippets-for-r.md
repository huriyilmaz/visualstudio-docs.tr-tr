---
title: R için kod parçacıkları
description: Visual Studio'da R için kod parçacıkları, rasgele uzunluktaki kod bloklarını hızla eklemek için kısayollar sağlar ve benzer kodu tekrar tekrar yeniden yazmaktan kaçınmanıza yardımcı olur.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 05a21da94dd643b04cea94b7840ca26d9379cb5a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969468"
---
# <a name="code-snippets"></a>Kod parçacıkları

Visual Studio'daki kod parçacıkları, rasgele uzunluktaki kod bloklarını hızla eklemek için kısayollar sağlar ve benzer kodu tekrar tekrar yeniden yazmaktan kaçınmanıza yardımcı olur. R Tools for Visual Studio (RTVS), Visual Studio'nun koleksiyonuna düzinelerce kullanışlı R snippet snippet ekler.

Bir parçacık eklemek için, snippet (IntelliSense sağlanır) kısaltılmış adını yazın, sonra eklemek için **Sekme** tuşuna basın.

Bazı basit örnekler:

- sonra `=` tab ve RTVS atama `<-` işleci ne genişletir yazın.
- türü `>` sonra Tab ve RTVS `%>%` boru işleci genişletir.

Parçacıklar karakterlerin karakter tamamlamadan çok daha fazlası olabilir. Örneğin, işlevli bir CSV dosyasını `read.csv` okumak için bir parçacık, adları veya parametreleri hatırlamak zorunda kalmanızı engelleyebilir:

![Read.csv için arama eklemek için kod snippet kullanmaanimasyonu](media/code-snippet-expansion.gif)

Bu durumda, yazarken, `readc`IntelliSense bir tamamlama listesi görüntüler. Açılan ve **basıldığında** bu tamamlanma yı seçer `readc`ve **Sekme'ye** yeniden basmak parçacığı genişletir. (Bu nedenle, parçacık genişletme genellikle "snippet yazın ve TAB iki kez basın" olarak düşünülmektedir). Çoğu durumda, ilk Sekme IntelliSense seçimini tamamlar ve ikinci Sekme genişlemeyi tetikler.

Kullanılabilir tüm parçacıkları görmek için **Araçlar** > **Kodu Parçacıkları Yöneticisi** iletişim kutusunu **(Ctrl**+**K**,**B**) açın ve **Dil**için **R'yi** seçin. Bir açıklama ve kısayol metnini görmek için grupları genişletin ve tek tek parçacıkları seçin:

![R için kod parçacıkları iletişim kutusu](media/code-snippet-dialog.png)

Özel kod parçacıkları oluşturmak için, Walkthrough'daki yönergeleri [izleyerek: Bir kod parçacığı oluşturun.](../ide/walkthrough-creating-a-code-snippet.md) Sonuçta, bir kod parçacığı sadece bir XML dosyasıdır. Örneğin, aşağıdaki kod boru işlemi (kısayol) `>`için parçacıktır:

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

Tüm kod parçacıkları için XML dosyaları RTVS ile yüklenir; **Kod Parçacıkları Yöneticisi'ndeki** **Konum** alanı yolu sağlar. Ayrıca [src/Package/Impl/Snippets](https://github.com/Microsoft/RTVS/tree/master/src/Package/Impl/Snippets)altında GitHub'daki RTVS kaynak kodunda bulabilirsiniz.
