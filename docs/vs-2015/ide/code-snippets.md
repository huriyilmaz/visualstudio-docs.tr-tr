---
title: Kod parçacıkları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- code snippets, replacement parameters
- code snippets, surround with
- replacement parameters
- code snippets, expansion
- surround with
- code snippets
ms.assetid: 85976ad9-4c9a-4e7b-896e-66ec6f955199
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5b41b6e4d4a7635b32edb5697c89ecb1249fb9da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619723"
---
# <a name="code-snippets"></a>Kod Parçacıkları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod parçacıkları, bağlam menüsü komutu veya kısayol tuşlarının birleşimini kullanarak bir kod dosyasına eklenebilen yeniden kullanılabilir kod bloklarında yer alabilir. Genellikle try-finally veya if-else blokları gibi yaygın olarak kullanılan kod blokları içerirler, ancak tüm sınıfları veya yöntemleri eklemek için kullanılabilirler.

## <a name="expansion-snippets-and-surround-with-snippets"></a>Genişleme parçacıkları ve surround-kod parçacıkları
 Visual Studio 'da, belirtilen bir ekleme noktasına eklenen ve kod parçacığı kısayolunun yanı sıra bir kod parçacığı kısayolunun (yalnızca C# ve C++) yerini alacak şekilde iki tür kod parçacığı vardır: genişletme parçacıkları.

 Ekleme kod parçacığına bir örnek: C# ' de, try-finally bloğu eklemek için tryf kısayolunun kullanılması:

```
try
{

}
finally
{

}

```

 Kod penceresinin bağlam menüsünde kod **parçacığı Ekle** ' ye tıklayıp sonra **Visual C#**' a, sonra `tryf` da YAZıP sekme `tryf` tuşuna basarak veya sekme + Tab tuşlarına basarak bu kod parçacığını ekleyebilirsiniz.

 Bir surround-kod parçacığı ile bir örnek: C++ ' da, `if` ekleme parçacığı ya da bir surround olarak kod parçacığı olarak kullanılabilir. Bir kod satırı seçer (örneğin `return FALSE;` ) ve ardından **Ile Çevrele**' ye tıklarsanız, parçacık satır etrafında **if**genişletilir:

```
if (true)
{
    return FALSE;
}

```

## <a name="snippet-replacement-parameters"></a>Kod parçacığı değiştirme parametreleri
 Kod parçacıkları, yazmakta olduğunuz kesin kodu sığdırmak için değiştirmeniz gereken yer tutucuları olan değiştirme parametrelerini içerebilir. Önceki örnekte `true` , uygun koşulla değiştireceğiniz bir değiştirme parametresidir. Yaptığınız değişiklik, kod parçacığında aynı değiştirme parametresinin her örneği için yinelenir.

 Örneğin, Visual Basic bir özelliği ekleyen bir kod parçacığı vardır. Kod penceresinin bağlam menüsünde **parçacığı Ekle** ' ye tıklayın, ardından **kod desenleri**, **Özellikler, yordamlar, olaylar**ve bir özellik tanımlayın. Aşağıdaki kod eklenir:

```
Private newPropertyValue As String
Public Property NewProperty() As String
    Get
        Return newPropertyValue
    End Get
    Set(ByVal value As String)
        newPropertyValue = value
    End Set
End Property

```

 `newPropertyValue`' A geçiş yaparsanız `m_property` , her örneği `newPropertyValue` değiştirilir. `String` `Int` Özelliğini özellik bildiriminde olarak değiştirirseniz, set yöntemindeki değer de olarak değiştirilir `Int` .

## <a name="code-snippet-manager"></a>Kod parçacığı Yöneticisi
 **Araçlar/kod parçacıkları Yöneticisi**' ne tıklayarak şu anda yüklü olan tüm kod parçacıklarını ve disk üzerindeki konumlarını görebilirsiniz. Kod parçacıkları dile göre görüntülenir.

 **Kod parçacıkları Yöneticisi** Iletişim kutusunda **ekleme** ve **kaldırma** düğmeleri ile kod parçacığı dizinleri ekleyebilir ve kaldırabilirsiniz. Bağımsız kod parçacıkları eklemek için **Içeri aktar** düğmesini kullanın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Izlenecek yol: kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md) [nasıl yapılır:](../ide/how-to-distribute-code-snippets.md) kod parçacıkları [Için en iyi](../ide/best-practices-for-using-code-snippets.md) kod parçacıkları dağıtım kod parçacıkları [sorun giderme parçacıkları](../ide/troubleshooting-snippets.md) [Visual C# kod parçacıkları](../ide/visual-csharp-code-snippets.md) [Visual C++ kod](../ide/visual-cpp-code-snippets.md) parçacıkları [kod parçacıkları şema başvurusu](../ide/code-snippets-schema-reference.md)
