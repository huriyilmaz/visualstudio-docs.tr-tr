---
title: R için kod parçacıkları
description: Visual Studio R için kod parçacıkları, rastgele uzunluktaki kod blokları hızla eklemek için kısayollar sağlar ve bu da benzer kodları yeniden yazmadan ve bunların üzerine yazmaya kaçınmanıza yardımcı olur.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: 53da9805458647803b9590818748f604d32c6bd1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100523"
---
# <a name="code-snippets-for-r"></a>R için kod parçacıkları

Visual Studio kod parçacıkları, rastgele uzunluktaki kod bloklarını hızlı bir şekilde eklemek için kısayollar sağlar ve bunlara benzer bir şekilde ve daha fazla kod yazmayı önlemenize yardımcı olur. Visual Studio için R Araçları (rtvs), Visual Studio koleksiyonuna onlarca yararlı R kod parçacıkları ekler.

Bir kod parçacığı eklemek için, kod parçacığının kısaltılmış adını (IntelliSense sağlanır) yazın ve sonra eklemek için **Tab** tuşuna basın.

Bazı basit örnekler:

- `=`ardından Tab yazın ve RTVS bunu `<-` atama işlecine genişletir.
- `>`ardından Tab yazın ve RTVS, `%>%` Kanal işleci genişletir.

Kod parçacıkları yalnızca karakterlerin karakter tamamından çok daha fazla olabilir. Bir CSV dosyasını işlevle okumak için bir kod parçacığı `read.csv` , örneğin, adları veya parametreleri anımsamak zorunda kalmadan sizi hatırlayabiliyor:

![read.csv çağrısı eklemek için kod parçacığı kullanmanın animasyonu](media/code-snippet-expansion.gif)

Bu durumda, siz yazarken `readc` , IntelliSense bir tamamlanma listesi görüntüler. Açılır listeden ve **Tab** tuşuna basarak bu tamamlamayı seçip `readc` , **sekme** tuşuna bir kez daha basıldığında kod parçacığı genişletilir. (Bu nedenle, kod parçacığı genişletmesi genellikle "parçacığı yazın ve TAB tuşuna iki kez bas" olarak düşünülebilir). Çoğu durumda, ilk sekme IntelliSense seçimini tamamlar ve ikinci sekme genişletmeyi tetikler.

Kullanılabilir tüm parçacıkları görmek için **Araçlar**  >  **kod parçacıkları Yöneticisi** iletişim kutusunu (**CTRL** + **K**,**B**) açın ve **dil** için **R** ' yi seçin. Bir açıklamayı ve kısayol metnini görmek için grupları genişletin ve bağımsız parçacıkları seçin:

![R için kod parçacıkları iletişim kutusu](media/code-snippet-dialog.png)

Özel kod parçacıkları oluşturmak için [Izlenecek yol: kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md)' ya yönelik yönergeleri izleyin. Sonuç olarak, bir kod parçacığı yalnızca bir XML dosyasıdır. Örneğin, aşağıdaki kod kanal işlemi (kısayol) için kod parçacıdır `>` :

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

Tüm kod parçacıkları için XML dosyaları RTVS; ile yüklenir **kod parçacıkları yöneticisindeki** **konum** alanı yolunu sağlar. ayrıca, [src/Package/ımpl/](https://github.com/Microsoft/RTVS/tree/master/src/Package/Impl/Snippets)parçacıklarıyla ilgili GitHub de rtvs kaynak kodunda bulabilirsiniz.
